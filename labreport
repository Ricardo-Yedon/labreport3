import org.eclipse.jetty.server.Server;
import org.eclipse.jetty.server.Request;
import org.eclipse.jetty.server.handler.AbstractHandler;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

public class StringServer extends AbstractHandler {
    private String message = "";

    public void handle(String target, Request baseRequest, HttpServletRequest request, HttpServletResponse response) throws IOException {
        response.setContentType("text/html;charset=utf-8");
        response.setStatus(HttpServletResponse.SC_OK);

        String path = request.getPathInfo();
        if (path.startsWith("/add-message")) {
            String query = request.getQueryString();
            if (query != null) {
                String[] pairs = query.split("=");
                if (pairs.length == 2 && pairs[0].equals("s")) {
                    String value = pairs[1];
                    message += "\n" + value;
                }
            }
        }

        response.getWriter().println(message);
        baseRequest.setHandled(true);
    }

    public static void main(String[] args) throws Exception {
        Server server = new Server(8080);
        server.setHandler(new StringServer());
        server.start();
        server.join();
    }
}
