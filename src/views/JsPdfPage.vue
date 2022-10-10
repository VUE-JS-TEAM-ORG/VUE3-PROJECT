<template>
  <div class="mycontenu">
    <button @click.prevent="exportPdf">pdf</button>
    <table class="mytable" id="header">
      <tr>
        <td class="mytable-td">
          <h2 class="titleHeader">Calibration Report</h2>
        </td>
      </tr>
    </table>
    <table class="mytable" id="info" style="font-size: 6;">
      <tr>
        <td class="mytable-td">Date : {{dataInfo.date }}</td>
      </tr>
      <tr>
        <td class="mytable-td">Operato : {{dataInfo.operator }}</td>
      </tr>
      <tr>
        <td class="mytable-td">Sopdft :{{dataInfo.sopdft }}</td>
      </tr>
      <tr>
        <td class="mytable-td">Issue : {{dataInfo.issue }}</td>
      </tr>
      <tr>
        <td class="mytable-td">AssayTest : {{dataInfo.assayTest }}</td>
      </tr>
      <tr>
        <td class="mytable-td">Comment : {{dataInfo.comment }}</td>
      </tr>
    </table>
    <table class="mytable" id="titleInformation">
      <tr>
        <td class="mytable-td">
            <h4>Component Information</h4>
        </td>
      </tr>
    </table>
    <table id="striped" class="table table-striped" style="width: 100%;padding-top: 100px;">
        <thead style="background:#2453c2;color:white;width: 100%;">
          <tr>
            <th >Component</th>
            <th >MaterialNumber</th>
            <th>LotNumber</th>
            <th >ExpirationDate</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="data in componentInformation" :key="data">
            <td> {{data.component }}</td>
            <td>{{data.materialNumber }}</td>
            <td>{{data.lotNumber }}</td>
            <td>{{data.expirationDate }}</td>
          </tr>
        </tbody>
    </table>
    <table class="mytable" id="titleAnalysis">
      <tr>
        <td class="mytable-td">
            <h4>Analysis Information</h4>
        </td>
      </tr>
    </table>
     <div class='row'>
        <table id="analysis" style="width: 50%;" class="column  table table-striped" >
          <tr v-for="data in analysisInformation" :key="data">
            <td>{{data.key}}</td>
            <td>{{data.value }}</td>
          </tr>
        </table>
        <table id="analysis" style="width: 50%;" class="column  table table-striped" >
          <tr v-for="data in analysisInformation" :key="data">
            <td>{{data.key}}</td>
            <td>{{data.value }}</td>
          </tr>
        </table>
     </div>
     <div class='row'>
          <div style="width: 49.5%;">
            <table class="myfooter" id="titleStandard">
              <tr>
                <td class="mytable-td">
                  <h3>Standard Information</h3>
                </td>
              </tr>
            </table>
            <table id="Standard" style="width: 100%;" class="column  table table-striped" >
              <tr v-for="data in standardInformation" :key="data">
                <td>{{data.key}}</td>
                <td>{{data.value }}</td>
              </tr>
            </table>
          </div>
          <div style="width: 49.5%;">
            <table class="mytable" id="titleSelection">
              <tr>
                <td class="mytable-td">
                   <h3>Channel Selection</h3>
                </td>
              </tr>
            </table>
            <table id="Selection"  style="width: 100%;" class="column table table-striped" >
              <tr v-for="data in channelSelection" :key="data">
                <td>{{data.key}}</td>
                <td>{{data.value }}</td>
              </tr>
            </table>
          </div>
     </div>

     <table class="mytable" id="titleCalibrations">
        <tr>
          <td class="mytable-td">
             <h4>Raw Data Calibrations</h4>
          </td>
        </tr>
     </table>
     <table id="Calibrations" class="table table-striped">
      <thead style="background: #2453c2;color:white;width: 100%;">
          <tr> 
            <th scope="col"><span style="width: 100%;height: 100%;">Concentration</span> </th>
            <th scope="col">Position</th>
            <th scope="col">TargetCt</th>
            <th scope="col">DeltaCt</th>
            <th scope="col">TiterCalced</th>
            <th scope="col">LogTiterCalced</th>
            <th scope="col">Types</th>
            <th scope="col">Invalid</th>
          </tr>
        </thead>
        <tbody>
          <tr  v-for="data in rawDataCalibrations1" :key="data">
            <td> {{data.concentration }}</td>
            <td>{{data.position }}</td>
            <td>{{data.targetCt }}</td>
            <td>{{data.deltaCt }}</td>
            <td>{{data.titerCalced }}</td>
            <td>{{data.logTiterCalced }}</td>
            <td>{{data.types }}</td>
            <td>{{data.invalid }}</td>
          </tr>
        </tbody>
     </table>
     <table class="mytable" id="Chart1">
        <tr>
          <td class="mytable-td">  
              <canvas id="myChart1" class="myChart"></canvas>
          </td>
        </tr>
     </table>
     <table class="mytable" id="Chart2">
        <tr>
          <td class="mytable-td">  
              <canvas id="myChart2" class="myChart"></canvas>
          </td>
        </tr>
     </table>
     <table class="mytable" id="titleCalibrations">
        <tr>
          <td class="mytable-td">
              <h4>Raw Data Calibration2</h4>
          </td>
        </tr>
     </table>
     <table id="Calibrations" class="table table-striped">
      <thead style="background: #2453c2;color:white;width: 100%;">
          <tr> 
            <th e="cscopol"><span style="width: 100%;height: 100%;">Concentration</span> </th>
            <th scope="col">Position</th>
            <th scope="col">TargetCt</th>
            <th scope="col">DeltaCt</th>
            <th scope="col">TiterCalced</th>
            <th scope="col">LogTiterCalced</th>
            <th scope="col">Types</th>
            <th scope="col">Invalid</th>
          </tr>
        </thead>
        <tbody>
          <tr  v-for="data in rawDataCalibrations2" :key="data">
            <td> {{data.concentration }}</td>
            <td>{{data.position }}</td>
            <td>{{data.targetCt }}</td>
            <td>{{data.deltaCt }}</td>
            <td>{{data.titerCalced }}</td>
            <td>{{data.logTiterCalced }}</td>
            <td>{{data.types }}</td>
            <td>{{data.invalid }}</td>
          </tr>
        </tbody>
     </table>
  </div>
</template>

<script>
import pdfMake from "pdfmake/build/pdfmake";
import pdfFonts from "pdfmake/build/vfs_fonts";
// import htmlToPdfmake from 'html-to-pdfmake';
pdfMake.vfs = pdfFonts.pdfMake.vfs;
// import Exporter from "vue-chartjs-exporter";
import jsPDF from 'jspdf'
import autoTable from 'jspdf-autotable';
import Chart from 'chart.js/auto';
import axios from "axios";

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      dataInfo : { },
      componentInformation: [],
      analysisInformation: [],
      standardInformation: [],
      channelSelection: [],
      layoutAndResultFiles: [],
      rawDataCalibrations1: [],
      rawDataCalibrations2: [],
    }
  },
  methods: {
    exportPdf() {
      const canvas1 = document.querySelector('#myChart1');
      const canvas2 = document.querySelector('#myChart2');
      const canvasImg1 = canvas1.toDataURL("image/png", 1.0);
      const canvasImg2 = canvas2.toDataURL("image/png", 1.0);
      const doc = new jsPDF('p', 'pt', 'letter')
      doc.autoTable({
                theme: "plain",
                html: '#info',
      });

      doc.autoTable({
          theme: "plain",
          html: '#titleInformation',
          margin:0,
          styles: { fontSize: 14, fontStyle: 'bold'}
      });
      
      autoTable(doc, { html: '#striped' }, 10, 50)

      doc.autoTable({
          theme: "plain",
          html: '#titleAnalysis',
          margin:0,
          styles: { fontSize: 14, fontStyle: 'bold'},
      });      


      autoTable(doc, { html: '#analysis' }, 10, 50)

      doc.autoTable({
          theme: "plain",
          html: '#titleStandard',
          margin:0,
          styles: {fontSize: 14, fontStyle: 'bold'}
      }); 
      autoTable(doc, { html: '#Standard' }, 10, 50)

      doc.autoTable({
          theme: "plain",
          html: '#titleSelection',
          margin:0,
          styles: {fontSize: 14,fontStyle: 'bold' },
      });
      autoTable(doc, { html: '#Selection' }, 10, 50)
      doc.autoTable({
          theme: "plain",
          html: '#titleLayout',
          margin:0,
          styles: {fontSize: 14, fontStyle: 'bold'},
      });
      autoTable(doc, { html: '#ResultFiles' }, 10, 50)
      doc.autoTable({
          theme: "plain",
          html: '#titleCalibrations',
          margin:0,
          styles: {  fontSize: 14,  fontStyle: 'bold' },
      });
      // autoTable(doc, { html: '#Calibrations' })


      var pageNumber = doc.internal.getNumberOfPages()
      doc.autoTable({
        startY: 240,
        showHead: 'firstPage',        tableWidth: 200,
        html:   '#Standard',
        styles: {  overflow: 'hidden'},
        margin: { left: 380 },
      });

      doc.setPage(pageNumber)

      doc.autoTable({
        startY: 240,        
        tableWidth: 200,
        showHead: 'firstPage',
        html:   '#Selection',
        styles: { overflow: 'hidden'},
        margin: { right: 888 },
      });
   
      

      // autoTable(doc.addImage(canvasImg1, 'png', 50, 50, 450, 300 ), { html: '#Chart1' })
      
      // autoTable(doc.addImage(canvasImg2, 'png', 10, 10, 450, 300 ), { html: '#Chart2' })
      doc.addPage();

      doc.addImage(canvasImg1, 'png', 50, 50, 450, 300)
      doc.addImage(canvasImg2, 'png', 50, 350, 450, 300)
     
      const pageCount = doc.internal.getNumberOfPages() ;//Total Page Number
      for(let i = 0; i < pageCount; i++) {
              doc.setPage(i);
              const pageSize = doc.internal.pageSize;
              const pageWidth = 520;
              const pageHeight = doc.height ? pageSize.height : pageSize.getHeight();
              let pageCurrent = doc.internal.getCurrentPageInfo().pageNumber; //Current Page
              // Header
              doc.setFontSize(15);
              doc.text('Calibration Report', 55, 20, { baseline: 'right',Roboto: 'bold'});
              doc.line(30, 30, 560, 30);
              doc.setLineWidth(400); 

              // Footer
              doc.setFontSize(10);
              doc.text('Created on Wednesday, June 22, 2022 at 05:42:02',345, pageHeight -50, { baseline: 'right' });
              doc.text(`Page - ${pageCurrent}of${pageCount}`,pageWidth , pageHeight - 33, { baseline: 'bottom' });
              doc.text("Kit Material No: 9500111990",45, pageHeight - 33, { baseline: 'right' });
              doc.text("Kit Lot No: JD2810 ",45, pageHeight - 50, { baseline: 'right' });
              doc.text("Calibration report generated by gCAT Software, Version 10.7.2.0",140, pageHeight - 13, { baseline: 'right' });
      }
      doc.save("hello.pdf")
    },
  },
  mounted (){

    const ctx1 = document.getElementById('myChart1');
    const ctx2 = document.getElementById('myChart2');
    const myChart1 = new Chart(ctx1, {
        type: 'line',
        data: {
            labels: [40, 60 , 80 , 100 , 120 , 140 , 160 ],
            datasets: [{
                label: '# of Votes',
                data: [6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16],
                backgroundColor: [
                'rgb(0, 0, 255)',

                ],
                borderColor: [
                    'rgb(0, 0, 255)',
                ],
                pointColor: "rgb(0, 0, 255)",

                borderWidth: 0,
                pointRadius: 4,

            }]
        },
        options: {
            scales: {
                y: {
                    beginAtZero: true,
                    setFontSize: 0,
                }
            }
        }
    });
    const myChart2 = new Chart(ctx2, {
        type: 'line',
        data: {
            labels: [40, 60 , 80 , 100 , 120 , 140 , 160 ],
            datasets: [{
                label: '# of Votes chart2',
                data: [6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16],
                backgroundColor: [
                'rgb(0, 0, 255)',

                ],
                borderColor: [
                    'rgb(0, 0, 255)',
                ],
                pointColor: "rgb(0, 0, 255)",

                borderWidth: 0,
                pointRadius: 4,

            }]
        },
        options: {
            scales: {
                y: {
                    beginAtZero: true,
                    setFontSize: 0,
                }
            }
        }
    });
    myChart1; 
    myChart2; 
    
  },
  async created() {
    try {
      const res = await axios.get(`http://localhost:3001/getdata`);
      console.log(res);

      this.dataInfo = res.data[0].dataInfo
      this.componentInformation = res.data[0].componentInformation
      this.analysisInformation = res.data[0].analysisInformation
      this.standardInformation = res.data[0].standardInformation
      this.channelSelection = res.data[0].channelSelection
      this.layoutAndResultFiles = res.data[0].layoutAndResultFiles
      this.rawDataCalibrations1 = res.data[0].rawDataCalibrations1  
      this.rawDataCalibrations2 = res.data[0].rawDataCalibrations2  

    } catch (error) {
      console.log(error);
    }
  },
}
</script>

<style scoped>
.mycontenu {
  width: 50%;
  margin: auto;
  font-family: sans-serif;
}
.titleHeader {
  width: 100%;
  border-bottom:2px solid black;
  display:inline-block;
  padding-left: 30px;
}

.myChart {
  width: 90% !important;
  height:320px !important;
  margin: auto;
}
.title{
    margin: 0;
    font-weight:400;
    color: #3a3232;
    font-size: 17px;
}
.title-info{
    font-weight: 400;
}
.table, td, th {
  border: 1px solid #cdc2c2;
}
.table {
  border-collapse: collapse;
  width: 100%;
}
.table th, td {
  text-align: left;
  padding: 8px;
}
.table tr:nth-child(even) {
  background-color: #f2f2f2;
}
.row {
  display: flex;
  gap: 10px;
}
.column {

}
.titleFooter {
  margin: 0;padding: 0;
}
.rowFooter {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  justify-content: space-between;
  margin-top: 10px;
}
.mytable{
  border: none !important;
  width: 100% !important;
}
.mytable-td{
  border: none !important;margin: 0%;padding: 0%;
}
</style>
