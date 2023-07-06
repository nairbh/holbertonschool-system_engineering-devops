classDiagram
    User --|> WebsiteVisitor
    WebsiteVisitor : +visitWebsite()

    class Server {
        -IP: 8.8.8.8
    }

    class WebServer {
        -server: Server
        +receiveRequest()
        +forwardRequest()
    }

    class ApplicationServer {
        -server: Server
        +processRequest()
        +retrieveApplicationFiles()
    }

    class ApplicationFiles {
        -codeBase
    }

    class Database {
        -server: Server
        +retrieveData()
    }

    class Domain {
        -name: foobar.com
        +configureDNS()
    }

    User --> WebServer
    WebServer --> ApplicationServer
    ApplicationServer --> ApplicationFiles
    ApplicationServer --> Database
    WebServer --> Domain
