<template>
  <g-gantt-chart
    :chart-start="chartStart"
    :chart-end="chartEnd"
    precision="month"
    :row-height="85"
    grid
    width="100%"
    bar-start="beginDate"
    bar-end="endDate"
    :date-format="format"
    @change-month="getMonth($event.changeType)"
    @click-bar="onClickBar($event.bar, $event.e, $event.datetime)"
    @mousedown-bar="onMousedownBar($event.bar, $event.e, $event.datetime)"
    @dblclick-bar="onMouseupBar($event.bar, $event.e, $event.datetime)"
    @mouseenter-bar="onMouseenterBar($event.bar, $event.e)"
    @mouseleave-bar="onMouseleaveBar($event.bar, $event.e)"
    @dragstart-bar="onDragstartBar($event.bar, $event.e)"
    @drag-bar="onDragBar($event.bar, $event.e)"
    @dragend-bar="onDragendBar($event.bar, $event.e, $event.movedBars)"
    @contextmenu-bar="onContextmenuBar($event.bar, $event.e, $event.datetime)"
  >
    <g-gantt-row push-on-overlap subtitle="piso" label="My row 1" :bars="bars1" highlight-on-hover />
    <g-gantt-row push-on-overlap subtitle="piso" label="My row 2" highlight-on-hover :bars="bars2" />
    <g-gantt-row push-on-overlap subtitle="piso" label="My row 3" highlight-on-hover :bars="bars3" />
    <g-gantt-row push-on-overlap subtitle="piso" label="My row 4" highlight-on-hover :bars="bars4" />
    <g-gantt-row push-on-overlap subtitle="piso" label="My row 5" highlight-on-hover :bars="bars5" />
    <g-gantt-row push-on-overlap subtitle="piso" label="My row 6" highlight-on-hover :bars="bars6" />
    <g-gantt-row push-on-overlap subtitle="piso" label="My row 7" highlight-on-hover :bars="bars7" />
    <g-gantt-row push-on-overlap subtitle="piso" label="My row 8" highlight-on-hover :bars="bars8" />
    <g-gantt-row push-on-overlap subtitle="piso" label="My row 9" highlight-on-hover :bars="bars9" />
    <g-gantt-row push-on-overlap subtitle="piso" label="My row 10" highlight-on-hover :bars="bars10" />
    <g-gantt-row push-on-overlap subtitle="piso" label="My row 11" highlight-on-hover :bars="bars11" />
  </g-gantt-chart>

  <button type="button" @click="addBar()">Add bar</button>
  <button type="button" @click="deleteBar()">Delete bar</button>
</template>

<script setup lang="ts">
import { ref } from "vue"
import type { GanttBarObject } from "./types.js"

const chartStart = ref("21.03.2021 12:00")
const chartEnd = ref("15.07.2021 12:00")
const format = ref("DD.MM.YYYY HH:mm")

const bars1 = ref<GanttBarObject[]>([
  {
    beginDate: "23.04.2021 13:00",
    endDate: "25.05.2021 19:00",
    ganttBarConfig: {
      id: "8621987329",
      label: "I'm in a bundle",
      bundle: "bundle2",
      hasHandles: true,
    }
  }
])
const bars3 = ref<GanttBarObject[]>([
  {
    beginDate: "24.04.2021 13:00",
    endDate: "25.05.2021 19:00",
    ganttBarConfig: {
      id: "3",
      label: "I'm in a bundle",
    }
  }
])
const bars4 = ref<GanttBarObject[]>([
  {
    beginDate: "24.04.2021 13:00",
    endDate: "25.05.2021 19:00",
    ganttBarConfig: {
      id: "4",
      label: "I'm in a bundle",
    }
  }
])
const bars5 = ref<GanttBarObject[]>([
  {
    beginDate: "24.04.2021 13:00",
    endDate: "25.05.2021 19:00",
    ganttBarConfig: {
      id: "5",
      label: "I'm in a bundle",
    }
  }
])
const bars6= ref<GanttBarObject[]>([
  {
    beginDate: "24.04.2021 13:00",
    endDate: "25.05.2021 19:00",
    ganttBarConfig: {
      id: "6",
      label: "I'm in a bundle",
    }
  }
])
const bars7 = ref<GanttBarObject[]>([
  {
    beginDate: "24.04.2021 13:00",
    endDate: "25.05.2021 19:00",
    ganttBarConfig: {
      id: "7",
      label: "I'm in a bundle",
    }
  }
])
const bars8 = ref<GanttBarObject[]>([
  {
    beginDate: "24.04.2021 13:00",
    endDate: "25.05.2021 19:00",
    ganttBarConfig: {
      id: "8",
      label: "I'm in a bundle",
    }
  }
])
const bars9 = ref<GanttBarObject[]>([
  {
    beginDate: "24.04.2021 13:00",
    endDate: "25.05.2021 19:00",
    ganttBarConfig: {
      id: "9",
      label: "I'm in a bundle",
    }
  }
])
const bars10 = ref<GanttBarObject[]>([
  {
    beginDate: "24.04.2021 13:00",
    endDate: "25.05.2021 19:00",
    ganttBarConfig: {
      id: "10",
      label: "I'm in a bundle",
    }
  }
])
const bars11 = ref<GanttBarObject[]>([
  {
    beginDate: "24.04.2021 13:00",
    endDate: "25.05.2021 19:00",
    ganttBarConfig: {
      id: "11",
      label: "I'm in a bundle",
    }
  }
])

const bars2 = ref([
  {
    beginDate: "21.04.2021 13:00",
    endDate: "25.05.2021 19:00",
    ganttBarConfig: {
      id: "1592311887",
      label: "I'm in a bundle",
      bundle: "bundle2",
      hasHandles: true,
      style: {
        background: "magenta",
      }
    }
  },
  {
    beginDate: "01.01.2021 00:00",
    endDate: "01.03.2021 00:00",
    ganttBarConfig: {
      id: "7716981641",
      label: "Lorem ipsum dolor",
      hasHandles: true,
      style: {
        background: "#b74b52"
      }
    }
  },
  {
    beginDate: "15.06.2021 00:00",
    endDate: "10.07.2021 00:00",
    ganttBarConfig: {
      id: "9716981641",
      label: "Oh hey",
      style: {
        background: "#69e064",
        borderRadius: "5px",
        color: "blue",
        fontSize: "10px"
      }
    }
  }
])
const addBar = () => {
  if (bars1.value.some((bar) => bar.ganttBarConfig.id === "test1")) {
    return
  }
  const bar = {
    beginDate: "26.02.2021 00:00",
    endDate: "26.03.2021 02:00",
    ganttBarConfig: {
      id: "test1",
      hasHandles: true,
      label: "Hello!",
      style: {
        background: "#5484b7",
        borderRadius: "20px"
      }
    }
  }
  bars1.value.push(bar)
}

const deleteBar = () => {
  const idx = bars1.value.findIndex((b) => b.ganttBarConfig.id === "test1")
  if (idx !== -1) {
    bars1.value.splice(idx, 1)
  }
}

const getMonth = (changeType: string) => {
  //console.log("cambie", changeType)
}
const onClickBar = (bar: GanttBarObject, e: MouseEvent, datetime?: string) => {
  //console.log("click-bar", bar, e, datetime)
}

const onMousedownBar = (bar: GanttBarObject, e: MouseEvent, datetime?: string) => {
  //console.log("mousedown-bar", bar, e, datetime)
}

const onMouseupBar = (bar: GanttBarObject, e: MouseEvent, datetime?: string) => {
  //console.log("mouseup-bar", bar, e, datetime)
}

const onMouseenterBar = (bar: GanttBarObject, e: MouseEvent) => {
  //console.log("mouseenter-bar", bar, e)
}

const onMouseleaveBar = (bar: GanttBarObject, e: MouseEvent) => {
  //console.log("mouseleave-bar", bar, e)
}

const onDragstartBar = (bar: GanttBarObject, e: MouseEvent) => {
  //console.log("dragstart-bar", bar, e)
}

const onDragBar = (bar: GanttBarObject, e: MouseEvent) => {
  //console.log("drag-bar", bar, e)
}

const onDragendBar = (
  bar: GanttBarObject,
  e: MouseEvent,
  movedBars?: Map<GanttBarObject, { oldStart: string; oldEnd: string }>
) => {
  //console.log("dragend-bar", bar, e, movedBars)
}

const onContextmenuBar = (bar: GanttBarObject, e: MouseEvent, datetime?: string) => {
  //console.log("contextmenu-bar", bar, e, datetime)
}
</script>
