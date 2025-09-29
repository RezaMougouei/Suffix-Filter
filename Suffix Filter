import java.io.BufferedReader;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.PrintWriter;
import java.util.*;

public class Suffix {

	/**
	 * Read lines one at a time from r.  After reading all lines, output
	 * to w each line that is not a suffix of any previously read line
	 * (ex: print the current line only if no earlier line ends with it).
	 * @param r the reader to read from
	 * @param w the writer to write to
	 * @throws IOException
	 */
	public static void doIt(BufferedReader r, PrintWriter w) throws IOException {
		HashSet<String> pref = new HashSet<>();
		boolean any = false;

		String line;
		while ((line = r.readLine()) != null) {
			if (line.isEmpty()) {
				if (!any) w.println("");
			} else {
				String rev = new StringBuilder(line).reverse().toString();
				if (!pref.contains(rev)) w.println(line);
				for (int k = 1; k <= rev.length(); k++)
					pref.add(rev.substring(0, k));
			}
			any = true;
		}
	}

	/**
	 * The driver.  Open a BufferedReader and a PrintWriter, either from System.in
	 * and System.out or from filenames specified on the command line, then call doIt.
	 * @param args
	 */
	public static void main(String[] args) {
		try {
			BufferedReader r;
			PrintWriter w;
			if (args.length == 0) {
				r = new BufferedReader(new InputStreamReader(System.in));
				w = new PrintWriter(System.out);
			} else if (args.length == 1) {
				r = new BufferedReader(new FileReader(args[0]));
				w = new PrintWriter(System.out);
			} else {
				r = new BufferedReader(new FileReader(args[0]));
				w = new PrintWriter(new FileWriter(args[1]));
			}
			long start = System.nanoTime();
			doIt(r, w);
			w.flush();
			long stop = System.nanoTime();
			System.out.println("Execution time: " + 1e-9 * (stop-start));
		} catch (IOException e) {
			System.err.println(e);
			System.exit(-1);
		}
	}
}
