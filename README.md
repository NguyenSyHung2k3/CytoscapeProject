# CytoscapeProject
## Sử dụng bộ thư viện chart Cytoscape.js cho hiển thị kết quả thuật toán sử dụng html, css, js trực tiếp <br>

Cytoscape.js là một thư viện đồ thị được viết bằng ngôn ngữ Javascript thuần cho phép hiển thị hình ảnh trực quan các mạng lưới đồ thị và hiển thị kết quả chạy của thuật toán <br>

Dưới đây là ví dụ về đồ thị Cytoscape đơn giản và hiển thị kết quả chạy thử của thuật toán Dijkstra
![Hình ảnh](https://github.com/NguyenSyHung2k3/CytoscapeProject/blob/main/Screenshot%202024-01-09%20111301.png)
## Vẽ đồ thị bằng Cytoscape.js
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
