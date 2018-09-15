# 13. Add simple NgRx spinner

## [Link to section slides](https://docs.google.com/presentation/d/1Y7Tf7kjO4Li0ihhkVgRjn4szFJPAkbMvilfrDCbrjq8/edit#slide=id.g2fa7fd70ec_0_1818)

## 1. npm i NgRx Store library

* npm install @ngrx/store

```text
npm i @ngrx/store
```

## 2.  Add a reducer

* Add a reducer with spinner state.

{% code-tabs %}
{% code-tabs-item title="src/app/state/spinner/spinner.reducer.ts" %}
```typescript
export function reducer(state = { isOn: false }, action) {
  switch (action.type) {
    case 'startSpinner': {
      return {
        isOn: true
      };
    }

    case 'stopSpinner': {
      return {
        isOn: false
      };
    }

    default:
      return state;
  }
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

## 3. Register NgRx in app module

* Add NgRx to AppModule

{% code-tabs %}
{% code-tabs-item title="src/app/app.module.ts" %}
```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { HttpClientModule } from '@angular/common/http';
import { RouterModule } from '@angular/router';

import { AppComponent } from './app.component';
import { HomeComponent } from './home/containers/home/home.component';
import { HttpClientInMemoryWebApiModule } from 'angular-in-memory-web-api';
import { StoreModule } from '@ngrx/store';

import { InMemoryDataService } from './app.db';
import { reducer } from './state/spinner/spinner.reducer';

@NgModule({
  declarations: [AppComponent, HomeComponent],
  imports: [
    BrowserModule,
    RouterModule.forRoot([
      { path: '', pathMatch: 'full', redirectTo: 'home' },
      { path: 'home', component: HomeComponent },
      { path: 'event', loadChildren: './event/event.module#EventModule' }
    ]),
    HttpClientModule,
    HttpClientInMemoryWebApiModule.forRoot(InMemoryDataService, { delay: 1000 }),
    StoreModule.forRoot({ spinner: reducer })
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule {}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

## 4. Inject store into the EventComponent

* Inject Store into the EventComponent.
* Select the spinner$ state.
* Dispatch a startSpinner and stopSpinner action when loading and receiving data from the fake backend.

{% code-tabs %}
{% code-tabs-item title="src/app/event/container/event/event.component.ts" %}
```typescript
import { Component, OnInit } from '@angular/core';
import { Observable } from 'rxjs';
import { Store, select } from '@ngrx/store';

import { Attendee } from '../../../models';
import { EventService } from '../../services/event.service';

@Component({
  selector: 'app-event',
  templateUrl: './event.component.html',
  styleUrls: ['./event.component.scss']
})
export class EventComponent implements OnInit {
  spinner$: Observable<boolean>;
  attendees$: Observable<Attendee[]>;

  constructor(private store: Store<any>, private eventService: EventService) {}

  ngOnInit() {
    this.getAttendees();
    this.spinner$ = this.store.pipe(select(state => state.spinner.isOn));
  }

  getAttendees() {
    this.attendees$ = this.eventService.getAttendees();
  }

  addAttendee(attendee: Attendee) {
    this.store.dispatch({ type: 'startSpinner' });
    this.eventService.addAttendee(attendee).subscribe(() => {
      this.store.dispatch({ type: 'stopSpinner' });
      this.getAttendees();
    });
  }
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

## 5. Update the EventComponent to show a basic loading indicator

* Add a loading div with an ngIf.
* Add a ngIf to the EventListComponent.

{% code-tabs %}
{% code-tabs-item title="src/app/event/containers/event.component.ts" %}
```markup
<app-add-attendee (addAttendee)="addAttendee($event)"></app-add-attendee>
<app-event-list *ngIf="!(spinner$ | async)" [attendees]="attendees$ | async"></app-event-list>
<div *ngIf="spinner$ | async">loading..</div>

```
{% endcode-tabs-item %}
{% endcode-tabs %}

![Image: Showing &apos;spinner&apos; state registered in AppModule and used in the component.](.gitbook/assets/image%20%287%29.png)

## StackBlitz Link

{% embed data="{\"url\":\"https://stackblitz.com/github/duncanhunter/angular-and-ngrx-demo-app/tree/13-simple-ngrx-spinner\",\"type\":\"link\",\"title\":\"StackBlitz\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"caption\":\"Web Link: Link to the demo app running in StackBlitz\"}" %}

