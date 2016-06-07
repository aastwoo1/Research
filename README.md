#Research
import java.util.ArrayList;
import java.util.List;
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.util.StringTokenizer;

public class Raster {
	private int rows;
	private int cols;
	
	
	public int getRows(){
		return this.rows;
	}
	
	public int getCols(){
		return this.cols;
	}
	
	public void setRows(int x){
		this.rows=x;
	
	}
	
	public void setCols(int x){
		this.cols=x;
	}

	
	public void setArray( BufferedReader x) throws IOException{
		//Get file and access lines
		String y = x.readLine();
        StringTokenizer st = new StringTokenizer(y);
        st.nextToken();
        String numOfColStr = st.nextToken();
        //access the number of columns
		this.cols = Integer.parseInt(numOfColStr);
		String z = x.readLine();
        StringTokenizer ss = new StringTokenizer(z);
        ss.nextToken();
        String numOfRowStr = ss.nextToken();
        //access the number of rows.
		this.rows = Integer.parseInt(numOfRowStr);
		//br.close();
	}
	
	public List <Double> oneRow(BufferedReader x) throws IOException{
		String line = x.readLine();
		StringTokenizer st = new StringTokenizer(line);
		List<Double> doubles = new ArrayList<Double>();
		while(st.hasMoreTokens()){
			String token = st.nextToken();
			Double d = Double.parseDouble(token);
			doubles.add(d);
		}
		
		//System.out.println(doubles);
		return doubles;
		
	}
	
	public Raster(String x) throws IOException{
		BufferedReader br = new BufferedReader(new FileReader(x));
		setArray(br);
		double[][] mapRas = new double[this.rows][this.cols];
		//skip the next 3 lines.
		int z = 0;
		while(z<3){
			br.readLine();
    		z++;
		}
		while(br != null){
			for (int i = 0; i < this.rows; i++) {
				List<Double> u = oneRow(br);
				System.out.println(u);
				for (int j = 0; j < this.cols; j++) {
					double get = u.get(j);
					System.out.println(get);
					mapRas[i][j]=get;
				}
		}
		
	}
		System.out.println("done");
		br.close();

	}
}



	

