# Fitness-LP

A good exploration of how the data would be structured in the app below.

May want to consider classes for some data items. However, how would I handle it when it's being pulled back from the database and is just JSON without the class methods?

## Using TypeScript

```typescript
// CONSTANTS

export enum Category {
  arms = 'Arms',
  back = 'Back',
  cardio = 'Cardio',
  chest = 'Chest',
  compound = 'Compound',
  core = 'Core',
  legs = 'Legs',
  shoulders = 'Shoulders',
  misc = 'Miscellaneous',
  event = 'Event',
  upperBody = 'Upper Body',
  lowerBody = 'Lower Body',
  fullBody = 'Full Body',
}

export enum Equipment {
  barbell = 'Barbell',
  dumbbell = 'Dumbbell',
  kettlebell = 'Kettlebell',
  plate = 'Plate',
  pullupBar = 'Pull-up Bar',
  cardioMachine = 'Cardio Machine',
  cableMachine = 'Cable Machine',
  weightMachine = 'Weight Machine',
  weightVest = 'Weight Vest',
  bands = 'Resistance Bands',
  chains = 'Chains',
}

export enum UnitPreference {
  imperial = 'Imperial',
  metric = 'Metric',
}

export enum DistanceConversion {
  kilometersToMiles = 0.621371,
  MilesToKilometers = 1.609344,
}

export enum WeightConversion {
  kilogramsToPounds = 2.204623,
  poundsToKilograms = 0.453592,
}

export enum HeightConversion {
  centimetersToInches = 0.393701,
  inchesToCentimeters = 2.54,
}

export enum Regex {
  email = '', // Use one from RegExr with 3.6 rating - It seems good
}

export enum AppLimits {
  workoutExercises = 100,
  exerciseSets = 100,
  name = 50,
  description = 300,
  note = 600,
}

export enum AppStorage {
  session,
  local,
}

export enum AppEntity {
  exercises = 'exercises',
  workouts = 'workouts',
  exerciseRecords = 'exerciseRecords',
  workoutRecords = 'workoutRecords',
  activeExerciseRecords = 'activeExerciseRecords',
  activeWorkoutRecords = 'activeWorkoutRecords',
  measurementRecords = 'measurementRecords',
}

const layout = 'Layout'

export enum Layout {
  default = 'Default' + layout,
  activeWorkout = 'ActiveWorkout' + layout,
}

const view = 'View'

export enum View {
  notFound = 'NotFound' + view,
  login = 'Login' + view,
  dashboard = 'Dashboard' + view,
  activeWorkout = 'ActiveWorkout' + view,
}
```

```typescript
// INTERFACES

export interface IUser {
  email: string,
  birthMonth: number,
  birthYear: number,
  height: IHeight,
}

export interface IExercise {
  name: string,
  description: string,
  previousRecordId: string,
  category: Category,
  equipment: Equipment[],
  hasSets: boolean,
  hasWeight: boolean,
  hasReps: boolean,
  hasDuration: boolean,
  hasDistance: boolean,
}

export interface IExerciseRecord {
  createdAt: string,
  note: string,
  exerciseId: string,
  sets: IExerciseSet[],
}

export interface IExerciseSet {
  weight: IWeight,
  reps: number,
  duration: number,
  distance: IDistance,
}

export interface Weight {
  kilograms: number,
  pounds: number,
}

export interface IDistance {
  kilometers: number,
  miles: number,
}

export interface IHeight {
  centimeters: number,
  inches: number,
}

export interface IWorkout {
  name: string,
  description: string,
  previousRecordId: string,
  exerciseIds: string[],
}

export interface IWorkoutRecord {
  createdAt: string,
  note: string,
  duration: number,
  workoutId: string,
}

export interface IMeasurementRecord {
  createdAt: string,
  note: string,
  bodyWeight: number,
  bodyFat: number,
  neck: number,
  shoulders: number,
  chest: number,
  biceps: number,
  forearms: number,
  waist: number,
  thighs: number,
  calves: number,
}
```

```typescript
// Dependency Injection

interface IMyComponentDependencies {
  databaseService: IDatabaseService
  storeService: IStoreService
}

// Figure out how all this has to work!
const dependencies = {
  databaseService: databaseThing(),
  storeService: storeThing(),
}

const myComponent({ dependencies: IMyComponentDependencies }) {
  dependencies.databaseService.doSomething()
  dependencies.storeService.doSomething()
}
```
