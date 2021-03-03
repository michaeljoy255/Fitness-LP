# Fitness-LP

A good exploration of how the data would be structured in the app below.

May want to consider classes for some data items. However, how would I handle it when it's being pulled back from the database and is just JSON without the class methods?

## Using TypeScript

```typescript
// CONSTANTS

export enum Category {
  arms: 'Arms',
  back: 'Back',
  cardio: 'Cardio',
  chest: 'Chest',
  compound: 'Compound',
  core: 'Core',
  legs: 'Legs',
  shoulders: 'Shoulders',
  misc: 'Miscellaneous',
  event: 'Event',
  upperBody: 'Upper Body',
  lowerBody: 'Lower Body',
  fullBody: 'Full Body',
}

export enum Equipment {
  barbell: 'Barbell',
  dumbbell: 'Dumbbell',
  kettlebell: 'Kettlebell',
  plate: 'Plate',
  pullupBar: 'Pull-up Bar',
  cardioMachine: 'Cardio Machine',
  cableMachine: 'Cable Machine',
  weightMachine: 'Weight Machine',
  weightVest: 'Weight Vest',
  bands: 'Resistance Bands',
  chains: 'Chains',
}

export enum UnitPref {
  imperial: 'Imperial',
  metric: 'Metric',
}

export enum DistanceConversion {
  kilometersToMiles: 0.621371,
  MilesToKilometers: 1.609344,
}

export enum WeightConversion {
  kilogramsToPounds: 2.204623,
  poundsToKilograms: 0.453592,
}

export enum HeightConversion {
  centimetersToInches: 0.393701,
  inchesToCentimeters: 2.54,
}

export enum Regex {
  email: '',
}

export enum AppLimits {
  workoutExercises: 100,
  exerciseSets: 100,
  name: 50,
  description: 300,
  note: 600,
}

export enum AppStorage {
  session,
  local,
}

export enum AppEntity {
  exercises: 'exercises',
  workouts: 'workouts',
  exerciseRecords: 'exerciseRecords',
  workoutRecords: 'workoutRecords',
  activeExerciseRecords: 'activeExerciseRecords',
  activeWorkoutRecords: 'activeWorkoutRecords',
  measurementRecords: 'measurementRecords',
}

const layout = 'Layout'

export enum Layout {
  default: 'Default' + layout,
  activeWorkout: 'ActiveWorkout' + layout,
}

const view = 'View'

export enum View {
  notFound: 'NotFound' + view,
  login: 'Login' + view,
  dashboard: 'Dashboard' + view,
  activeWorkout: 'ActiveWorkout' + view,
}
```

```typescript
// INTERFACES

export interface User {
  email: string,
  birthMonth: number,
  birthYear: number,
  height: Height,
}

export interface Exercise {
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

export interface ExerciseRecord {
  createdAt: string,
  note: string,
  exerciseId: string,
  sets: ExerciseSet[],
}

export interface ExerciseSet {
  weight: Weight,
  reps: number,
  duration: number,
  distance: Distance,
}

export interface Weight {
  kilograms: number,
  pounds: number,
}

export interface Distance {
  kilometers: number,
  miles: number,
}

export interface Height {
  centimeters: number,
  inches: number,
}

export interface Workout {
  name: string,
  description: string,
  previousRecordId: string,
  exerciseIds: string[],
}

export interface WorkoutRecord {
  createdAt: string,
  note: string,
  duration: number,
  workoutId: string,
}

export interface MeasurementRecord {
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
