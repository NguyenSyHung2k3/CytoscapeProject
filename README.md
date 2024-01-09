# CytoscapeProject
## Sử dụng bộ thư viện chart Cytoscape.js cho hiển thị kết quả thuật toán sử dụng html, css, js trực tiếp <br>

Cytoscape.js là một thư viện đồ thị được viết bằng ngôn ngữ Javascript thuần cho phép hiển thị hình ảnh trực quan các mạng lưới đồ thị và hiển thị kết quả chạy của thuật toán <br>

Dưới đây là ví dụ về đồ thị Cytoscape đơn giản và hiển thị kết quả chạy thử của thuật toán Dijkstra
![Hình ảnh](https://github.com/NguyenSyHung2k3/CytoscapeProject/blob/main/Screenshot%202024-01-09%20111301.png)
## Vẽ đồ thị bằng Cytoscape.js
* Khởi tạo cytoscape
```
let cy = cytoscape({

        container: $('.cy'), // container to render in
      
        elements: [ // list of graph elements to start with
          // { group: 'nodes',data: { id: 'n1' }, position: { x: 200, y: 100 } },
          // { group: 'nodes',data: { id: 'n2' }, position: { x: 100, y: 50 } },
          // { group: 'edges',data: { id: 'e0', source: 'n1', target: 'n2' } }
        ],
      
        style: [ // the stylesheet for the graph
          {
            selector: 'node',
            style: {
              'background-color': '#69e',
              'label': 'data(id)',
            }
          },
      
          {
            selector: 'edge',
            style: {
              'width': 1,
              'line-color': '#369',
              'target-arrow-color': '#369',
              'target-arrow-shape': 'triangle',
              'label': 'data(label)',
              'font-size': '14px',
              'color': '#777'
            }
          }
        ],
      
        style: cytoscape.stylesheet()
        .selector('edge')
            .css({
              'width': 3,
              'line-color': '#369',
              'target-arrow-color': '#369',
              'target-arrow-shape': 'triangle',
              'label': 'data(label)',
              'font-size': '14px',
              'color': '#777'
            })
          .selector('node')
            .css({
              'content': 'data(id)',
              'text-valign': 'center',
              'color': 'white',
              'text-outline-width': 2,
              'text-outline-color': '#888',
              'background-color': '#888'
            })
          .selector(':selected')
            .css({
              'background-color': 'black',
              'line-color': 'black',
              'target-arrow-color': 'black',
              'source-arrow-color': 'black',
              'text-outline-color': 'black'
            }),
      
        layout: {
          name: 'grid',
          rows: 1
        }
      
      });
```
* Thêm các Element vào trong đồ thị
```
cy.add([
          { group: 'nodes',data: { id: 'n1', name:'n11' }, position: { x: 50, y: 200 } },
          { group: 'nodes',data: { id: 'n2' }, position: { x: 131, y: 226 } },
          { group: 'nodes',data: { id: 'n3' }, position: { x: 128, y: 143 } },
          { group: 'nodes',data: { id: 'n4' }, position: { x: 249, y: 142 } },
          { group: 'nodes',data: { id: 'n5' }, position: { x: 191, y: 62 } },
          { group: 'nodes',data: { id: 'n6' }, position: { x: 66, y: 83 } },
          { group: 'edges',data: { id: 'e0', source: 'n1', target: 'n2', label: 7 } },
          { group: 'edges',data: { id: 'e1', source: 'n2', target: 'n3', label: 10 } },
          { group: 'edges',data: { id: 'e2', source: 'n1', target: 'n6', label: 14 } },
          { group: 'edges',data: { id: 'e3', source: 'n1', target: 'n3', label: 9 } },
          { group: 'edges',data: { id: 'e4', source: 'n2', target: 'n4', label: 15 } },
          { group: 'edges',data: { id: 'e5', source: 'n3', target: 'n4', label: 11 } },
          { group: 'edges',data: { id: 'e6', source: 'n3', target: 'n6', label: 2 } },
          { group: 'edges',data: { id: 'e7', source: 'n6', target: 'n5', label: 9 } },  
          { group: 'edges',data: { id: 'e8', source: 'n5', target: 'n4', label: 6 } },
      ]);
```
* Duyệt đồ thị bằng thuật toán Dijkstra có sẵn trong thư viện
```
var dijkstra = cy.elements().dijkstra('#n1', function(edge){
        return edge.data('label');
      });
      console.log( dijkstra.pathTo( cy.$('#n5') ));
      console.log( dijkstra.distanceTo( cy.$('#n5') ));
      var p = dijkstra.pathTo( cy.$('#n5') );
```
Thuật toán duyệt từ đỉnh n1 đến n5 và cho ra quãng đường đi bé nhất là 20.
