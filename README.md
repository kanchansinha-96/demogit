# demogit
def buildUrl = env.BUILD_URL
def matcher = buildUrl =~ /\/job\/API-Products\/job\/([^\/]+)/

def jobName = ""
if (matcher.find()) {
    jobName = matcher.group(1)
} else {
    echo "Could not extract job name from URL: ${buildUrl}"
    return null
}

def channelUrl = props[jobName]
