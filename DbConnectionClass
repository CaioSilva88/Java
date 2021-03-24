package pacote1;

import java.sql.Connection;
import java.sql.DriverManager;
import java.util.Calendar;

import com.mysql.jdbc.PreparedStatement;





public class Main {
	
	private static Main conexaoUtil;
	public static Main getInstance() {
		
		if(conexaoUtil==null) {
			
			conexaoUtil = new Main();
			
		}
		return conexaoUtil;
	}
	
	//variavel de conexao
	public static Connection createConnectionToMySQL() throws Exception {
		Class.forName("com.mysql.jdbc.Driver");
		Connection connection = DriverManager.getConnection("jdbc:mysql://localhost:3307/AV2","root","");
		return connection;
	}
	
	public static void main(String[] args) throws Exception {
		Connection con = createConnectionToMySQL();
		
		//testar seh null
		if(con!=null) {
			System.out.println("Conexao estabelecida");
			con.close();
		}else {
			System.out.println("Deu ruim");
		}
		
		
		
		String sql = "INSERT INTO usuario(nome, emal, endereco, dataHora) VALUES (?, ?, ?, ?)";
		Connection conn = null;
		PreparedStatement pstm = null;
		Contato contato = new Contato();
		
		try {
			//criar conexao com o bd
			conn = Main.createConnectionToMySQL();
			//criamos uma prepared... para executar query
			pstm = (PreparedStatement) conn.prepareStatement(sql);
			
			pstm.setString(1, "Caio");
			pstm.setString(2, "aaaaaaaa");
			pstm.setString(3, "bbbbbbb");
			pstm.setDate(4, new java.sql.Date(Calendar.getInstance().getTimeInMillis()));
			//executar a query
			pstm.execute();
			System.out.println("Dados cadastrados com SUCESSO.");
			
		}catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
			System.out.println("Erro");
		}finally {
			//fechar conn
			try {
				if(pstm!=null) {
					pstm.close();
				}
				if(conn!=null) {
					conn.close();
				}
			}catch (Exception e) {
				e.printStackTrace();
				// TODO: handle exception
			}
		}
		
		
	}
	

}
