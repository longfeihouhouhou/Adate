<style>
    ul, li {
        list-style: none;
    }

    .comp-full-calendar {
        padding: 20px;
        background: #fff;
        max-width: 960px;
        margin: 0 auto;
    }

    .comp-full-calendar ul, .comp-full-calendar p {
        margin: 0;
        padding: 0;
        font-size: 14px;
    }

    .full-calendar-header {
        display: flex;
        align-items: center;
    }

    .full-calendar-header .header-left, .full-calendar-header .header-right {
        flex: 1;
    }

    .full-calendar-header .header-center {
        flex: 3;
        text-align: center;
        font-weight: bold;
        font-size: 16px;
    }

    .full-calendar-header .header-center .title {
        margin: 0 10px;
    }

    .full-calendar-header .header-center .prev-month, .full-calendar-header .header-center .next-month {
        cursor: pointer;
    }

    .full-calendar-body {
        margin-top: 20px;
    }

    .full-calendar-body .weeks {
        display: flex;
        border: 1px solid rgb(32, 160, 255);
        background: rgb(32, 160, 255);
        min-height: 30px;
        padding-top: 3px;
    }

    .full-calendar-body .weeks .week {
        flex: 1;
        text-align: center;
        border-right: 1px solid #e0e0e0;
    }

    .full-calendar-body .weeks .week {
        flex: 1;
        text-align: center;
        border-right: 1px solid #e0e0e0;
    }

    .full-calendar-body .weeks strong {
        font-weight: bold;
        font-size: 14px;
        color: #fff;
    }

    .full-calendar-body .weeks strong:last-child {
        border-right: none;
    }

    .full-calendar-body .dates {
        position: relative;
    }

    .full-calendar-body .dates .week-row {
        border-left: 1px solid #e0e0e0;
        display: flex;
    }

    .full-calendar-body .dates .week-row .day-cell {
        flex: 1;
        min-height: 100px;
        padding: 4px;
        border-right: 1px solid #e0e0e0;
        border-bottom: 1px solid #e0e0e0;
    }

    .full-calendar-body .dates .week-row .day-cell .day-number {
        text-align: right;
    }

    .full-calendar-body .dates .week-row .day-cell.today {
        background-color: #fcf8e3;
    }

    .full-calendar-body .dates .week-row .day-cell.not-cur-month .day-number {
        color: rgba(0, 0, 0, 0.24);
    }

    .full-calendar-body .dates .dates-events {
        position: absolute;
        top: 0;
        left: 0;
        z-index: 1;
        width: 100%;
    }

    .full-calendar-body .dates .dates-events .events-week {
        display: flex;
    }

    .full-calendar-body .dates .dates-events .events-week .events-day {
        cursor: pointer;
        flex: 1;
        min-height: 109px;
        text-overflow: ellipsis;
        position: relative;

    }

    .full-calendar-body .dates .dates-events .events-week .events-day .day-number {
        text-align: right;
        padding: 4px 5px 4px 4px;
        opacity: 0;
    }

    .full-calendar-body .dates .dates-events .events-week .events-day.not-cur-month .day-number {
        color: rgba(0, 0, 0, 0.24);
    }

    .full-calendar-body .dates .dates-events .events-week .events-day .event-box .event-item {
        cursor: pointer;
        font-size: 12px;
        background-color: #C7E6FD;
        margin-bottom: 2px;
        color: rgba(0, 0, 0, 0.87);
        padding: 0 0 0 4px;
        height: 18px;
        line-height: 18px;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
        text-align: center;
    }

    .full-calendar-body .dates .dates-events .events-week .events-day .event-box .event-item.is-start {
        margin-left: 4px;
    }

    .full-calendar-body .dates .dates-events .events-week .events-day .event-box .event-item.is-end {
        margin-right: 4px;
    }

    .full-calendar-body .dates .dates-events .events-week .events-day .event-box .event-item.is-opacity {
        opacity: 0;
    }

    .full-calendar-body .dates .dates-events .events-week .events-day .event-box .more-link {
        cursor: pointer;
        padding-left: 8px;
        padding-right: 2px;
        color: rgba(0, 0, 0, 0.38);
        font-size: 14px;
    }

    .full-calendar-body .dates .more-events {
        position: absolute;
        width: 150px;
        z-index: 2;
        border: 1px solid #eee;
        box-shadow: 0 2px 6px rgba(0, 0, 0, 0.15);
    }

    .full-calendar-body .dates .more-events .more-header {
        background-color: #eee;
        padding: 5px;
        display: flex;
        align-items: center;
        font-size: 14px;
    }

    .full-calendar-body .dates .more-events .more-header .title {
        flex: 1;
    }

    .full-calendar-body .dates .more-events .more-header .close {
        margin-right: 2px;
        cursor: pointer;
        font-size: 16px;
    }

    .full-calendar-body .dates .more-events .more-body {
        height: 140px;
        overflow: hidden;
    }

    .full-calendar-body .dates .more-events .more-body .body-list {
        height: 120px;
        padding: 5px;
        overflow: auto;
        background-color: #fff;
    }

    .full-calendar-body .dates .more-events .more-body .body-list .body-item {
        cursor: pointer;
        font-size: 12px;
        background-color: #C7E6FD;
        margin-bottom: 2px;
        color: rgba(0, 0, 0, 0.87);
        padding: 0 0 0 4px;
        height: 18px;
        line-height: 18px;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }

    .full-calendar-body .lists {
        position: relative;
        border-width: 1px;
        border-style: solid;
        border-color: #e9e9ec;
    }

    .full-calendar-body .lists .list-table {
        table-layout: auto;
    }

    .full-calendar-body .lists table {
        width: 100%;
        box-sizing: border-box;
        table-layout: fixed;
        border-collapse: collapse;
        border-spacing: 0;
        font-size: 1em;
    }

    .full-calendar-body .lists tr {
        display: table-row;
        vertical-align: inherit;
        border-color: inherit;
    }

    .full-calendar-body .lists .list-table .list-header {
        border-bottom-width: 1px;
        background: #eee;
        font-size: 14px;
        color: #100d1d;
    }

    .full-calendar-body .lists .list-table a {
        color: #100d1d;
    }

    .full-calendar-body .lists .list-table td {
        border-width: 1px 0 0;
        padding: 8px 14px;
    }

    .full-calendar-body .lists .list-table .list-header .list-header-main {
        float: left;
    }

    .full-calendar-body .lists .list-table .list-header .list-header-alt {
        float: right;
    }

    .full-calendar-body .lists .list-table tr:first-child td {
        border-top-width: 0;
    }

    .full-calendar-body .lists .list-table .list-item {
        box-sizing: content-box;
    }

    .fc-list-item-time {
        padding-right: 0;
        width: 25%;
    }

    .fc-list-item-marker {
        padding-right: 0;
        width: 10px;
    }

    .fc-list-item-title {
        padding-right: 0;
    }

    .fc-event-dot {
        display: inline-block;
        width: 10px;
        height: 10px;
        border-radius: 5px;
        background-color: #3a87ad
    }

    .list-item:hover td {
        background-color: #f5f5f5;
    }

    ul.popover {
        position: absolute;
        padding: 5px;
        top: 60px;
        left: 0;
        line-height: 20px;
        width: 260px;
        background: rgb(32, 160, 255);
        color: #fff;
        display: none;
    }

    .popover span {
        margin-right: 5px;
    }

</style>
<template>
    <div class="comp-full-calendar">
        <div class="full-calendar-header">
            <div class="header-center">
                <!-- <span class="prev-month" @click="fPrevMonth">&lt;</span>-->
                <span class="title">{{title}}</span>
                <!-- <span class="next-month" @click="fNextMonth">&gt;</span>-->
            </div>
        </div>
        <div class="full-calendar-body">
            <div class="weeks" v-show="sundayFirst">
                <strong class="week">周日</strong>
                <strong class="week">周一</strong>
                <strong class="week">周二</strong>
                <strong class="week">周三</strong>
                <strong class="week">周四</strong>
                <strong class="week">周五</strong>
                <strong class="week">周六</strong>
            </div>

            <div class="weeks" v-show="!sundayFirst">
                <strong class="week">周一</strong>
                <strong class="week">周二</strong>
                <strong class="week">周三</strong>
                <strong class="week">周四</strong>
                <strong class="week">周五</strong>
                <strong class="week">周六</strong>
                <strong class="week">周日</strong>
            </div>

            <div class="dates" v-show="fMonthShow">
                <div class="dates-bg">
                    <div class="week-row" v-for="items in currentDates">
                        <div v-for="item in items"
                             :class="{'day-cell': true, today: item.isToday, 'not-cur-month': !item.isCurMonth  }">
                            <p class="day-number">{{item.monthDay}}</p>
                        </div>
                    </div>
                </div>
                <div class="dates-events" v-show="fMonthShow">
                    <div class="events-week" v-for="items in currentDates">
                        <div v-for="item in items" track-by="$index"
                             :class="{'events-day': true,today: item.isToday, 'not-curMonth': !item.isCurMonth  }"
                             v-pop-switch
                             @click="dayClicked($event, item.monthDay, item.isCurMonth)"
                        >
                            <p class="day-number">{{item.monthDay}}</p>
                            <div v-for="event in item.events" class="event-box" v-show="item.isCurMonth">
                                <p class="event-item">{{event.title}}</p>
                                <ul :class="{popover: item.events.length && item.isCurMonth}">
                                    <li v-for="detail in event.details">
                                        <span>{{detail.amount}}</span>
                                        <span>{{detail.code}}</span>
                                        <span>{{detail.type}}</span>
                                        <span>{{detail.date}}</span>
                                        <span>{{detail.state}}</span>
                                    </li>
                                </ul>
                            </div>

                        </div>
                    </div>
                </div>
            </div>
            <div class="lists" v-show="fListShow">
                <table class="list-table">
                    <tbody>
                    <template v-for="item in currentEvents">
                        <tr class="list-header" v-if="item.isHeader">
                            <td colspan="3">
                                <a class="list-header-main">{{item.time}}</a>
                                <a class="list-header-alt">{{item.date}}</a>
                            </td>
                        </tr>
                        <tr class="list-item" v-if="!item.isHeader">
                            <td class="fc-list-item-time fc-widget-content">{{item.time}}</td>
                            <td class="fc-list-item-marker fc-widget-content">
                                <span class="fc-event-dot"></span>
                            </td>
                            <td class="fc-list-item-title fc-widget-content">
                                <a>{{item.title}}</a>
                            </td>
                        </tr>
                    </template>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script type="text/ecmascript-6">
    function getMousePos(event) {
        var e = event || window.event;
        return {'x': e.clientX, 'y': e.clientY}
    }
    export default {
        data () {
            return {
                fListShow: false,
                fMonthShow: true,
                fToDayDisabled: true
                // currentDate: new Date()
            }
        },
        props: {
            events: {
                type: Array,
                default: []
            },
            sundayFirst: {
                type: Boolean,
                default: true
            },
            currentDate: {
                type: Date,
                default: () => {
                    return new Date()
                }
            }
        },
        computed: {
            title: {
                get: function () {
                    var date = this.currentDate;
                    return date.getFullYear() + "-" + (1 + date.getMonth());
                }
            },
            currentDates: function () {
                return this.getCalendar();
            },
            currentEvents: function () {
                return this.getCalList();
            }
        },
        methods: {
            fToDay(event){
                event.stopPropagation();
                this.fListShow = false;
                this.fMonthShow = true;
                this.fToDayDisabled = true;
                this.currentDate = new Date();
                //console.log(event.target.tagName + " -- " + this._format(this.currentDate, "yyyy-MM-dd"));
            },
            fPrevMonth(event){
                event.stopPropagation();
                this.fToDayDisabled = false;
                this.fListShow = false;
                this.fMonthShow = true;
                this.currentDate = this.changeMonth(this.currentDate, -1);
                //console.log(event.target.tagName + " -- " + this._format(this.currentDate, "yyyy-MM-dd"));
            },
            fNextMonth(event){
                event.stopPropagation();
                this.fToDayDisabled = false;
                this.fListShow = false;
                this.fMonthShow = true;
                this.currentDate = this.changeMonth(this.currentDate, 1);
                //console.log(event.target.tagName + " -- " + this._format(this.currentDate, "yyyy-MM-dd"));
            },
            changeMonth: function changeMonth(date, num) {
                var dt = new Date(date);
                return new Date(dt.setMonth(dt.getMonth() + num));
            },
            getCalendar() {
                var now = new Date(); // today
                var current = new Date(this.currentDate);
                var startDate = this._getStartDate(current);
                var curWeekDay = startDate.getDay();
                // begin date of this table may be some day of last month
                // startDate.setDate(startDate.getDate() - curWeekDay + 1);  这一行让周日排在最后
                startDate.setDate(startDate.getDate() - curWeekDay); //不加1可以让周日排在第一天

                //setDate方法传0设置为上个月最后一天，传-1则是上个月倒数第二天，以此类推，当为2月时传-2就是1月29号

                //getDay()  0（周日） 到 6（周六）
                //getDate() 1 ~ 31
                //getFullYear()
                //getMonth() 月份 (0 ~ 11)
                var calendar = [];
                for (var perWeek = 0; perWeek < 6; perWeek++) {
                    var week = [];
                    for (var perDay = 0; perDay < 7; perDay++) {
                        week.push({
                            monthDay: startDate.getDate(),
                            isToday: now.toDateString() == startDate.toDateString(),
                            isCurMonth: startDate.getMonth() == current.getMonth(),
                            weekDay: perDay,
                            date: new Date(startDate),
                            events: this.slotEvents(startDate)
                        });

                        startDate.setDate(startDate.getDate() + 1);
                    }
                    calendar.push(week);
                }
                return calendar;
            },
            _getStartDate: function (date) {
                // return first day of this month
                return new Date(date.getFullYear(), date.getMonth(), 1);
            },
            _getEndDate: function (date) {
                // get last day of this month
                var dt = new Date(date.getFullYear(), date.getMonth() + 1, 1); // 1st day of next month
                return new Date(dt.setDate(dt.getDate() - 1)); // last day of this month
            },
            slotEvents: function (date) {
                // find all events start from this date
                var cellIndexArr = [];
                var thisDayEvents = this.events.filter(function (day) {
                    var dt = new Date(day.start);
                    var st = new Date(dt.getFullYear(), dt.getMonth(), dt.getDate());
                    var ed = day.end ? new Date(day.end) : st;
                    // console.log('slotEvt', st, ed, date)
                    return date >= st && date <= ed;
                    //这里的表现是如果有一天是连续的，如一个活动从1号持续到10号，那么1号到10直接的每一天都会限时该活动，已达到延续几日的效果
                });
                if (thisDayEvents.length > 0) { //这一段是有用的，当一天有多件事情的时候有用，根据每件事的用时排序，长的排在前面
                    // sort by duration
                    thisDayEvents.sort(function (a, b) {
                        var at = new Date(a.start);
                        var bt = new Date(b.start);
                        return at.getTime() - bt.getTime();
//                    if (!a.cellIndex) return 1;
//                    if (!b.cellIndex) return -1;
//                    return a.cellIndex - b.cellIndex;
                    });
                }
                // mark cellIndex and place holder
                for (var i = 0; i < thisDayEvents.length; i++) {
                    thisDayEvents[i].cellIndex = thisDayEvents[i].cellIndex || i + 1;
                    thisDayEvents[i].isShow = true;
                    if (thisDayEvents[i].cellIndex == i + 1 || i > 2) continue;
                    thisDayEvents.splice(i, 0, {
                        title: 'holder',
                        cellIndex: i + 1,
                        start: this._format(date, 'yyyy-MM-dd'),
                        end: this._format(date, 'yyyy-MM-dd'),
                        isShow: false
                    });
                }
                //console.log(JSON.stringify(thisDayEvents))

                return thisDayEvents;
            },
            getCalList: function getCalList() {
                var thisEventList = this.events;
                thisEventList.sort(function (a, b) {
                    var at = new Date(a.start);
                    var bt = new Date(b.start);
                    return at.getTime() - bt.getTime();
                });
                var eventList = [];
                var perDate = null;
                var weeks = ["星期日", "星期一", "星期二", "星期三", "星期四", "星期五", "星期六"];
                var _format = this._format;
                var _getFullHourName = this._getFullHourName;
                var _isSameDay = this._isSameDay;
                thisEventList.forEach(function (item, index, array) {
                    var at = new Date(item.start);
                    var addHeader = false;
                    if (perDate != null) {
                        if (_isSameDay(perDate, at)) {
                            addHeader = false;
                        } else {
                            addHeader = true;
                        }
                    } else {
                        addHeader = true;
                    }
                    if (addHeader) {
                        eventList.push({
                            isHeader: true,
                            time: weeks[at.getDay()],
                            title: '',
                            date: _format(at, 'yyyy-MM-dd')
                        });
                    }
                    eventList.push({
                        isHeader: false,
                        time: _getFullHourName(at) + " - " + _getFullHourName(new Date(item.end)),
                        title: item.title,
                        date: _format(at, 'yyyy-MM-dd')
                    });
                    perDate = at;
                });
                return eventList;
            },
            _isSameDay(now, current){
                return (now.getFullYear() == current.getFullYear()
                && now.getMonth() == current.getMonth()
                && now.getDate() == current.getDate());
            },
            _getFullHourName(date){
                var h = date.getHours();
                var m = date.getMinutes();
                return ((h < 10) ? "0" + h : "" + h) + ":" + ((m < 10) ? "0" + m : "" + m) + (h > 12 ? "pm" : "am");
            },
            _getHourName(date){
                return date.getHours() > 12 ? "pm" : "am";
            },
            _format: function (date, _format) {
                if (typeof date === 'string') {
                    date = new Date(date.replace(/-/g, '/'));
                } else {
                    date = new Date(date);
                }

                var map = {
                    'M': date.getMonth() + 1,
                    'd': date.getDate(),
                    'h': date.getHours(),
                    'm': date.getMinutes(),
                    's': date.getSeconds(),
                    'q': Math.floor((date.getMonth() + 3) / 3),
                    'S': date.getMilliseconds()
                };

                _format = _format.replace(/([yMdhmsqS])+/g, function (all, t) {
                    var v = map[t];
                    if (v !== undefined) {
                        if (all.length > 1) {
                            v = '0' + v;
                            v = v.substr(v.length - 2);
                        }
                        return v;
                    } else if (t === 'y') {
                        return String(date.getFullYear()).substr(4 - all.length);
                    }
                    return all;
                });
                return _format;
            },
            dayClicked(e, today, isCur) {
                if (!isCur) return false;
                let n = this.currentDate;
                let d = new Date(n.getFullYear(), n.getMonth(), today);
                this.$emit('dayClicked', {date: d});
            }
        },
        directives: {
            popSwitch: {
                componentUpdated: (el) => {
                    let pop = el.getElementsByClassName('popover');
                    el.onmouseenter = function (e) {
                        if (!pop.length) return false;
                        pop[0].style.display = 'block';
                    };
                    el.onmouseleave = function (e) {
                        if (!pop.length) return false;
                        pop[0].style.display = 'none';
                    }
                }
            }
        }
    }
</script>
