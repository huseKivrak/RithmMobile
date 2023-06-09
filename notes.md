# gameplan
1. login to mobile app with rithm creds
2. make api call to rithm proper
    -> authenticate on backend,
3. render appropriate info in mobile UI


## rithm api > urls.py:
    urlpatterns = [
    path('-openapi', get_schema_view(
        title="Student Information System API",
        description="""\
API for our Student Information System. The API is cohort-specific; it
shows only things related to the cohort.

For non-admin users, it shows only public information; for admin users,
it also shows private information.

This is the documentation version of this API; you can also visit the
[browsable version](/api/).
        """,
        version="1.0.0"
    ), name='openapi-schema'),
    path('-docs/', TemplateView.as_view(
        template_name='swagger-ui.html',
        extra_context={'schema_url': reverse_lazy('openapi-schema')}
    ), name='swagger-ui'),
    path('-auth/', include('rest_framework.urls')),
    path('-token/', obtain_auth_token),
    path('-new-app', new_app),
    path('', include(router.urls)),
]

    1. POST http://.../api/-token
        ({"username", "password"})
        -> {
	"token": "7a6d68f87739ccca8c46c5fc6e4c0aa35339253f"
    2. ???

    - look up most secure library for session management
    - can hardcode token to get things up and running


# UI
## show only today's events
    1. get LectureSession, Exercise, Event where start_at = today
    2. Sort all three
    3. Display
 ### Date options
    - Date as state (on mount, setDate = Date.now())
        -> each "swipe" increments date state by one; logic is consistent
        "(getCurrentLectures(date state))"
    - third-party library


## Rithm styling ideas:
- $primary: rgb(228, 107, 102); or #E46B66
- tint primary: #f3bcb9
- $font-family-base: "Source Serif Pro";

- Banner at top: same white/off white color of phone
+ Rithm logo
+ search bar
+ your account icon

- Nav at bottom:
+ Home
+