<template>
  <div>
    <v-stepper v-model="stepModel">
      <v-stepper-header>
        <template
          v-for="(step, index) in stepsArr"
        >
          <v-stepper-step
            :key="'stepperHeaderKey' + step.key"
            :step="step.stepIndex"
            editable
          >
            {{ step.title }}
          </v-stepper-step>

          <v-divider
            v-if="index !== stepsArr.length - 1"
            :key="'stepperDividerKey' + step.key"
          />

        </template>
      </v-stepper-header>
  
      <v-stepper-items>
        <v-stepper-content
          v-for="step in stepsArr"       
          :step="step.stepIndex"
          :key="'stepperContentKey' + step.key"
        >
          <component
            v-model="savedValues[step.key]"
            :is="step.component"
          />
        </v-stepper-content>
      </v-stepper-items>


    </v-stepper>
  </div>
</template>

<script>
import Component1 from '../components/Component1'
import Component2 from '../components/Component2'
import Component3 from '../components/Component3'
import Component4 from '../components/Component4'
import Component5 from '../components/Component5'
import Component6 from '../components/Component6'

export default {
  name: 'IndexPage',

  components: {
    Component1,
    Component2,
    Component3,
    Component4,
    Component5,
    Component6,
  },

  data () {
    return {
      stepModel: 1,

      savedValues: {
        component1: '',
        component2: '',
        component3: [],
        component4: '',
        component5: '',
        component6: '',
      },
    }
  },

  computed: {
    stepsArr () {
      const steps = [
        { key: 'component1', title: 'Component 1', component: 'Component1' },
        { key: 'component2', title: 'Component 2', component: 'Component2' },
        { key: 'component3', title: 'Component 3', component: 'Component3' },
      ]

      const optionalSteps = [
        { key: 'component4', title: 'Component 4', component: 'Component4' },
        { key: 'component5', title: 'Component 5', component: 'Component5' },
        { key: 'component6', title: 'Component 6', component: 'Component6' },
      ]

      for (const optionalStep of optionalSteps) {
        if (this.savedValues.component3.includes(optionalStep.key)) {
          steps.push(optionalStep)
        }
      }

      return steps.map((step, index) => ({
        ...step,
        stepIndex: index + 1,
      }))
    },
  },
}
</script>
