---
tags: Log
aliases: 
  - 
cssclass:
---

## Day Planner
```mermaid
gantt
    dateFormat  HH-mm
    axisFormat %H:%M
    %% Current Time: 12:02:18 PM
    section Tasks
    START     :07-30, 510mm
    END     :16-00, 0mm
    section Breaks

```

- [ ] 07:30 START
- [ ] 16:00 END

## On This Day...

[[2020-<%tp.date.now("MM-DD")%>]]

---
[[<%tp.date.yesterday("YYYY-MM-DD")%>]] <== <button class="date_button_today">Today</button> ==> [[<%tp.date.tomorrow("YYYY-MM-DD")%>]]

<%* if (tp.date.now("M") == 1 & tp.date.now("D") < 5) { %>
- [ ] Do Annual Review
<%* } %>
<%* if (tp.date.now("D") < 6) { %>
- [ ] Do Monthly Review
<%* } %>
<%* if (tp.date.now("ddd") == "Fri") { %>
- [ ] Do Weekly Review
<%* } %>
