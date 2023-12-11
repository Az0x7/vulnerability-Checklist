id: exposing-django-debug-panel
info:
  name: Exposing Django Debug Panel and Sensitive Infrastructure Information
  author: aliend89
  severity: high
  reference: https://hackerone.com/reports/2078707

http:
  - method: GET
    path:
      - "{{BaseURL}}//app/tmp/healthcheck.json"
      - "{{BaseURL}}/fxa-rp-events"
    matchers:
      - type: word
        words:
          - "ADMIN_ENABLED"
          - "ALLOWED_HOSTS"
          - "AUTHENTICATION_BACKENDS"
          - "AUTH_USER_MODEL"
          - "AVATAR_IMG_SRC"
          - "AWS_REGION"
          - "AWS_SES_CONFIGSET"
          - "AWS_SNS_TOPIC"
          - "AWS_SQS_EMAIL_QUEUE_URL"
          - "AWS_SQS_QUEUE_URL"
          - "BASKET_ORIGIN"
          - "BUNDLE_PLAN_ID_US"
          - "CACHES"
          - "CORS_ALLOWED_ORIGINS"
          - "DATABASES"
          - "INSTALLED_APPS"
          - "INTERNAL_IPS"
          - "LOGGING"
          - "REST_FRAMEWORK"

      - type: status
        status:
          - 200
