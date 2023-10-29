Nama		: Almas Diqya Wafa’
NIM		: 5311421005
Prodi		: Teknik Elektro
Mata Kuliah	: Artificial Intellegent and Aplication
Rombel	: Senin 09.00

MODUL 4
“Teknik Pencarian Blind Search”

3.	Ubahlah method static void main sehingga bentuk tree seperti Gambar 4.6 dapat dibentuk. Kemudian tentukan bagaimana algoritma BFS dapat menemukan node 9. Program:
import java.util.ArrayDeque; 
import java.util.ArrayList; 
import java.util.HashMap; 
import java.util.List; 
import java.util.Map; 
import java.util.Queue; 
import java.util.Set; 

public class AdjacencyList 
{ 
public enum NodeColour { WHITE, GRAY, BLACK } 
public static class Node 
{ 
int data; 
int distance; 
NodeColour colour; 
public Node(int data) 
{ 
            this.data = data; 
        } 
        
    /**
     *
     * @return
     */
    @Override
        public String toString() 
        { 
         return "(" + data + ",d=" + distance + ")"; 
        } 
    } 
    
    Map<Node, List<Node>> nodes; 
 
    public AdjacencyList() 
    { 
        nodes = new HashMap<>(); 
    } 
    
    public void addEdge(Node n1, Node n2) 
    { 
        if (nodes.containsKey(n1)) { 
            nodes.get(n1).add(n2); 
        } else { 
       ArrayList<Node> list = new ArrayList<>(); 
            list.add(n2); 
            nodes.put(n1, list); 
        } 
    } 
    
    public void bfs(Node s) 
    { 
        Set<Node> keys = nodes.keySet(); 
        for (Node u : keys) { 
            if (u != s) { 
                u.colour = NodeColour.WHITE; 
                u.distance = Integer.MAX_VALUE; 
            } 
        } 
        s.colour = NodeColour.GRAY; 
        s.distance = 0; 
        Queue<Node> q = new ArrayDeque<>(); 
        q.add(s); 
        while (!q.isEmpty()) { 
            Node u = q.remove(); 
            List<Node> adj_u = nodes.get(u); 
            if (adj_u != null) { 
                for (Node v : adj_u) { 
                    if(v.colour == NodeColour.WHITE) { 
                        v.colour = NodeColour.GRAY; 
                        v.distance = u.distance + 1; 
                        q.add(v); 
                    } 
                } 
            } 
            u.colour = NodeColour.BLACK; 
            System.out.print(u + " "); 
        } 
    } 
    public static void main(String[] args) { 
    AdjacencyList graph = new AdjacencyList(); 
    Node n1 = new Node(1); 
    Node n2 = new Node(2); 
    Node n3 = new Node(3); 
    Node n4 = new Node(4); 
    Node n5 = new Node(5); 
    Node n6 = new Node(6); 
    Node n7 = new Node(7); 
    Node n8 = new Node(8); 
    Node n9 = new Node(9); 
    Node n10 = new Node(10); 
    Node n11 = new Node(11); 
    Node n12 = new Node(12); 
    
    graph.addEdge(n1, n2); 
    graph.addEdge(n1, n3); 
    graph.addEdge(n1, n4); 
    graph.addEdge(n2, n1); 
    graph.addEdge(n2, n5); 
    graph.addEdge(n2, n6); 
    graph.addEdge(n3, n1); 
    graph.addEdge(n4, n1);
    graph.addEdge(n4, n7); 
    graph.addEdge(n4, n8);
    graph.addEdge(n5, n2); 
    graph.addEdge(n5, n9);
    graph.addEdge(n5, n10); 
    graph.addEdge(n5, n6);
    graph.addEdge(n6, n2); 
    graph.addEdge(n6, n5);
    graph.addEdge(n7, n4); 
    graph.addEdge(n7, n11); 
    graph.addEdge(n7, n12); 
    graph.addEdge(n7, n8); 
    graph.addEdge(n8, n4);
    graph.addEdge(n8, n7); 
    graph.addEdge(n9, n5);
    graph.addEdge(n9, n10); 
    graph.addEdge(n10, n5);
    graph.addEdge(n10, n9); 
    graph.addEdge(n11, n7);
    graph.addEdge(n11, n12); 
    graph.addEdge(n12, n7);
    graph.addEdge(n12, n11);    
    
    graph.bfs(n1); 
    }
}

Hasil:
Setelah melakukan praktikum menggunakan software Netbeans dan melakukan uji coba pada Modul 4 (nomor 3) ditemukan hasil sebagai berikut.
(1,d=0) (2,d=1) (3,d=1) (4,d=1) (5,d=2) (6,d=2) (7,d=2) (8,d=2) (9,d=3) (10,d=3) (11,d=3) (12,d=3) BUILD SUCCESSFUL (total time: 0 seconds)

Penjelasan:
Dalam program di atas, algoritma BFS dimulai dari simpul 1 (n1) dan menjelajahi graf sesuai dengan hubungan yang telah ditentukan. Berikut adalah penjelasan langkah-langkah algoritma BFS untuk menemukan node 9:

1. *Node 1 (d=0):* BFS dimulai dari simpul n1 dengan jarak 0.
2. *Node 2 (d=1):* n1 memiliki tiga anak, yaitu n2, n3, dan n4. BFS melanjutkan ke n2 dengan jarak 1.
3. *Node 3 (d=1):* n1 juga memiliki anak n3, tetapi n3 sudah diwarnai GRAY, jadi BFS tidak melanjutkan ke n3.
4. *Node 4 (d=1):* n1 juga memiliki anak n4, tetapi n4 sudah diwarnai GRAY, jadi BFS tidak melanjutkan ke n4.
5. *Node 5 (d=2):* n2 memiliki dua anak, yaitu n5 dan n6. BFS melanjutkan ke n5 dengan jarak 2.
6. *Node 6 (d=2):* n2 juga memiliki anak n6, tetapi n6 sudah diwarnai GRAY, jadi BFS tidak melanjutkan ke n6.
7. *Node 7 (d=2):* n4 memiliki dua anak, yaitu n7 dan n8. BFS melanjutkan ke n7 dengan jarak 2.
8. *Node 8 (d=2):* n4 juga memiliki anak n8, tetapi n8 sudah diwarnai GRAY, jadi BFS tidak melanjutkan ke n8.
9. *Node 9 (d=3):* n5 memiliki dua anak, yaitu n9 dan n10. BFS melanjutkan ke n9 dengan jarak 3.

Dengan demikian, algoritma BFS pada graf di atas menemukan node 9 dengan jarak 3 dari node awal (n1).


