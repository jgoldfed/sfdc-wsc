# Introduction #

This page shows how to use WSC from GAE.

# Details #

  * copy wsc-XX.jar, partner-XX.jar and wsc-gae.jar to the /war/WEB-INF/lib/ directory of the GAE war file.

  * Set GAE as transport for on WSC ConnectorConfig:
> > config.setTransport(GaeHttpTransport.class);

  * Here is a full working example:

```

import java.io.IOException;
import javax.servlet.http.*;
import com.google.appengine.api.users.User;
import com.google.appengine.api.users.UserService;
import com.google.appengine.api.users.UserServiceFactory;

import com.sforce.soap.partner.wsc.*;
import com.sforce.soap.partner.sobject.wsc.*;
import com.sforce.ws.*;
import com.sforce.ws.transport.GaeHttpTransport;

public class GuestbookServlet extends HttpServlet {

    public void doGet(HttpServletRequest req, HttpServletResponse resp)
              throws IOException {
        UserService userService = UserServiceFactory.getUserService();
        User user = userService.getCurrentUser();

        if (user != null) {
            resp.setContentType("text/plain");
            resp.getWriter().println("Hello, " + user.getNickname() + callSfdc());
        } else {
            resp.sendRedirect(userService.createLoginURL(req.getRequestURI()));
        }
    }


    private String callSfdc() {

        try {
        ConnectorConfig config = new ConnectorConfig();
        config.setTransport(GaeHttpTransport.class);
        config.setUsername("username");
        config.setPassword("password");
        config.setTraceMessage(true);

        PartnerConnection connection = Connector.newConnection(config);
        SObject account = new SObject();
        account.setType("Account");
        account.setField("Name", "My Account from gae");
        return "result " + connection.create(new SObject[]{account})[0];
        } catch(ConnectionException e) {
           return "failed " + e;
        }
   }
}


```