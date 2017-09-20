```shell
sh 'curl -s http://[YOUR_JENKINS_IP]:[YOUR_JENKINS_PORT]/job/[YOUR_JOB_NAME]/${BUILD_NUMBER}/configSubmit -X POST --data-urlencode "json={\'displayName\':\'#${BUILD_NUMBER}\', \'description\':\'hogehoge\'}"'
```
