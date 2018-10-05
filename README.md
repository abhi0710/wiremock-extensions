# wiremock-extensions

Contains the extension for bodyFileName templating.

eg:
{
    "request": {
        "method": "GET",
        "urlPattern": "/some/thing\\?test=.*"
    },
    "response": {
        "status": 200,
        "bodyFileName": "{{request.path.[0]}}_{{request.requestLine.query.test}}.json",
        "headers": {
            "Content-Type": "text/plain"
        },
        "transformers": ["response-template","response-body-filename-template"]
    }
}

In this case if http://localhost:8181/some/thing?test=query is hit, content of file from ./__files/some_query.json 
is returned

If the content is again templated, Values will be replaced in that also.
