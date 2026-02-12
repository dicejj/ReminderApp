4. classDiagram
    class User {
        +int UserID
        +string Email
        +string Preferences
        +Login()
        +UpdateSettings()
    }

    class Event {
        +string Title
        +DateTime StartTime
        +DateTime EndTime
        +string Link
        +Create()
        +Edit()
        +Delete()
    }

    class CalendarManager {
        +List~Event~ AllEvents
        +MergeCalendars()
        +GetUpcomingEvents()
    }

    class ICalendarProvider {
        <<interface>>
        +Connect()
        +FetchEvents()
    }

    class GoogleCalendar {
        +ApiKey string
        +FetchEvents()
    }

    class CanvasCalendar {
        +ApiKey string
        +FetchEvents()
    }

    class AIChatbot {
        +string CurrentContext
        +SendMessage(string prompt)
        +UploadFile(File resource)
        +GenerateStudyPlan()
    }

    class LLMService {
        +string APIKey
        +SendRequest()
        +ParseResponse()
    }

    class NotificationSystem {
        +SendEmail()
        +SendSMS()
        +ScheduleReminder()
    }

    class DatabaseContext {
        +SaveUserKeys()
        +RetrieveUserKeys()
    }

    %% Relationships
    User "1" --> "1" CalendarManager : Uses
    User "1" --> "1" AIChatbot : Interacts with
    CalendarManager "1" --> "*" Event : Manages
    CalendarManager "1" --> "*" ICalendarProvider : Aggregates
    ICalendarProvider <|.. GoogleCalendar : Implements
    ICalendarProvider <|.. CanvasCalendar : Implements
    AIChatbot ..> CalendarManager : Reads/Modifies
    AIChatbot --> LLMService : Uses
    CalendarManager ..> NotificationSystem : Triggers
    CalendarManager --> DatabaseContext : Persists Data# ReminderApp
