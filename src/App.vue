<template>
  <ejs-gantt :dataSource="data"
             :taskFields="taskFields"
             :treeColumnIndex="1"
             :taskMode="scheduleMode"
             :enableCriticalPath="true"
             :highlightWeekends="true"
             :workWeek="weekdays"
             :holidays="leaveDetails"
             :eventMarkers="events"
             :allowUnscheduledTasks="true"
             :height="450">
    <e-columns>
      <e-column field="TaskID" headerText="Task ID" width="100" textAlign="Right"></e-column>
      <e-column field="TaskName" headerText="Task Name" textAlign="Left" width="200"></e-column>
      <e-column field="StartDate" headerText="Start Date" textAlign="Right" format="dd/MM/yyyy" width="120"></e-column>
      <e-column field="Duration" headerText="Duration" textAlign="Right" width="120"></e-column>
    </e-columns>
  </ejs-gantt>
</template>

<script>
import {GanttComponent, ColumnsDirective, ColumnDirective, DayMarkers, CriticalPath} from '@syncfusion/ej2-vue-gantt'
import {projectNewData} from './data.js'
export default {
  name: 'App',
  components: {
    'ejs-gantt': GanttComponent,
    'e-columns': ColumnsDirective,
    'e-column': ColumnDirective
  },
  provide:{
    gantt: [DayMarkers, CriticalPath]
  },
  data(){
    return{
      data: projectNewData,
      scheduleMode: 'Custom',
      events:[
        {
          day: new Date("04/02/2019")
        },
        {
          day: new Date("04/09/2019"),
          label: "Design Phase"
        }
      ],
      leaveDetails: [
        {
          from: new Date('04/05/2019'),
          to: new Date('04/06/2019'),
          label: 'Good Friday'
        },
        {
            from: new Date('04/11/2019'),
            label: 'Local Holiday'
        },
        {
            from: new Date('05/01/2019'),
            label: 'May Day'
        },
      ],
      weekdays: ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'],
      taskFields:{
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        endDate: 'EndDate',
        duration: 'Duration',
        progress: 'Progress',
        dependency: 'Predecessor',
        child: 'subtasks',
        manual: 'isManual',
        indicators: 'Indicators'
      },
    }
  }
}
</script>

<style>
@import url("https://cdn.syncfusion.com/ej2/material.css");
</style>
