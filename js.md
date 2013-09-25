
# Ajax

Core:

    request = new XMLHttpRequest()
    request.onreadystatechange = fn
    request.open('GET', url)
    request.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')
    request.send(null)
    
    response.responseXML
    response.responseText

readyState:

    0   init
    1   specified address
    2   sent request
    3   pending
    4   response received
                            
