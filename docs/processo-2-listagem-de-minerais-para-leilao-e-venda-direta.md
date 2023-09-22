### 3.3.2 Processo 2 – Listagem de Minerais para leilão e venda direta

```bpmn
<?xml version="1.0" encoding="UTF-8"?>
<bpmn:definitions xmlns:bpmn="http://www.omg.org/spec/BPMN/20100524/MODEL" xmlns:bpmndi="http://www.omg.org/spec/BPMN/20100524/DI" xmlns:dc="http://www.omg.org/spec/DD/20100524/DC" xmlns:di="http://www.omg.org/spec/DD/20100524/DI" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:modeler="http://camunda.org/schema/modeler/1.0" id="Definitions_0r8998u" targetNamespace="http://bpmn.io/schema/bpmn" exporter="Camunda Modeler" exporterVersion="5.14.0" modeler:executionPlatform="Camunda Cloud" modeler:executionPlatformVersion="8.2.0">
  <bpmn:collaboration id="Collaboration_111keer">
    <bpmn:participant id="Participant_0mkx5e2" name="Listagem de Minerais para leilão e venda direta" processRef="Process_1gyw4pm" />
  </bpmn:collaboration>
  <bpmn:process id="Process_1gyw4pm" isExecutable="true">
    <bpmn:laneSet id="LaneSet_0kze2hv">
      <bpmn:lane id="Lane_05tmfu3" name="Fornecedor">
        <bpmn:flowNodeRef>StartEvent_1</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_0vdzca6</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_11m3g9g</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Gateway_0rg37q4</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Gateway_05jngkn</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_0v2womw</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Gateway_1byvnuk</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Event_1l7ify3</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1t4e1ln</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_0gmykdh</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Event_05v77ir</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_0w3jhxx</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_01932vz</bpmn:flowNodeRef>
      </bpmn:lane>
    </bpmn:laneSet>
    <bpmn:startEvent id="StartEvent_1">
      <bpmn:outgoing>Flow_0uugwqr</bpmn:outgoing>
    </bpmn:startEvent>
    <bpmn:userTask id="Activity_0vdzca6" name="Criar nova listagem">
      <bpmn:incoming>Flow_0uugwqr</bpmn:incoming>
      <bpmn:outgoing>Flow_0tnse4q</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:userTask id="Activity_11m3g9g" name="Adicionar detalhes do item">
      <bpmn:incoming>Flow_0tnse4q</bpmn:incoming>
      <bpmn:outgoing>Flow_0dl6cef</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:exclusiveGateway id="Gateway_0rg37q4">
      <bpmn:incoming>Flow_0dl6cef</bpmn:incoming>
      <bpmn:outgoing>Flow_19plbaz</bpmn:outgoing>
      <bpmn:outgoing>Flow_06gtxfj</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:exclusiveGateway id="Gateway_05jngkn">
      <bpmn:incoming>Flow_021e3gl</bpmn:incoming>
      <bpmn:outgoing>Flow_1d3wt2s</bpmn:outgoing>
      <bpmn:outgoing>Flow_1xaeyg4</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:userTask id="Activity_0v2womw" name="Criar ou selecionar lote">
      <bpmn:incoming>Flow_19plbaz</bpmn:incoming>
      <bpmn:outgoing>Flow_021e3gl</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:exclusiveGateway id="Gateway_1byvnuk">
      <bpmn:incoming>Flow_06gtxfj</bpmn:incoming>
      <bpmn:incoming>Flow_12awwmo</bpmn:incoming>
      <bpmn:incoming>Flow_155qcvf</bpmn:incoming>
      <bpmn:outgoing>Flow_0qgdkl4</bpmn:outgoing>
      <bpmn:outgoing>Flow_1cezeva</bpmn:outgoing>
      <bpmn:outgoing>Flow_1rt5bfh</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:endEvent id="Event_1l7ify3">
      <bpmn:incoming>Flow_1nj6hz6</bpmn:incoming>
    </bpmn:endEvent>
    <bpmn:serviceTask id="Activity_1t4e1ln" name="Salvar  item">
      <bpmn:incoming>Flow_0qgdkl4</bpmn:incoming>
    </bpmn:serviceTask>
    <bpmn:serviceTask id="Activity_0gmykdh" name="Salvar item como rascunho">
      <bpmn:incoming>Flow_1cezeva</bpmn:incoming>
      <bpmn:outgoing>Flow_1nj6hz6</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:endEvent id="Event_05v77ir">
      <bpmn:incoming>Flow_1rt5bfh</bpmn:incoming>
    </bpmn:endEvent>
    <bpmn:userTask id="Activity_0w3jhxx" name="Adicionar data de início e fim">
      <bpmn:incoming>Flow_1d3wt2s</bpmn:incoming>
      <bpmn:outgoing>Flow_12awwmo</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:userTask id="Activity_01932vz" name="Selecionar lote futuro">
      <bpmn:incoming>Flow_1xaeyg4</bpmn:incoming>
      <bpmn:outgoing>Flow_155qcvf</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:sequenceFlow id="Flow_0uugwqr" sourceRef="StartEvent_1" targetRef="Activity_0vdzca6" />
    <bpmn:sequenceFlow id="Flow_0tnse4q" sourceRef="Activity_0vdzca6" targetRef="Activity_11m3g9g" />
    <bpmn:sequenceFlow id="Flow_0dl6cef" sourceRef="Activity_11m3g9g" targetRef="Gateway_0rg37q4" />
    <bpmn:sequenceFlow id="Flow_19plbaz" sourceRef="Gateway_0rg37q4" targetRef="Activity_0v2womw" />
    <bpmn:sequenceFlow id="Flow_06gtxfj" sourceRef="Gateway_0rg37q4" targetRef="Gateway_1byvnuk" />
    <bpmn:sequenceFlow id="Flow_021e3gl" sourceRef="Activity_0v2womw" targetRef="Gateway_05jngkn" />
    <bpmn:sequenceFlow id="Flow_1d3wt2s" sourceRef="Gateway_05jngkn" targetRef="Activity_0w3jhxx" />
    <bpmn:sequenceFlow id="Flow_1xaeyg4" sourceRef="Gateway_05jngkn" targetRef="Activity_01932vz" />
    <bpmn:sequenceFlow id="Flow_12awwmo" sourceRef="Activity_0w3jhxx" targetRef="Gateway_1byvnuk" />
    <bpmn:sequenceFlow id="Flow_155qcvf" sourceRef="Activity_01932vz" targetRef="Gateway_1byvnuk" />
    <bpmn:sequenceFlow id="Flow_0qgdkl4" sourceRef="Gateway_1byvnuk" targetRef="Activity_1t4e1ln">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'Dados Preenchidos'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:sequenceFlow id="Flow_1cezeva" sourceRef="Gateway_1byvnuk" targetRef="Activity_0gmykdh">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'Dados Incompletos'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:sequenceFlow id="Flow_1rt5bfh" sourceRef="Gateway_1byvnuk" targetRef="Event_05v77ir" />
    <bpmn:sequenceFlow id="Flow_1nj6hz6" sourceRef="Activity_0gmykdh" targetRef="Event_1l7ify3" />
    <bpmn:textAnnotation id="TextAnnotation_17584va">
      <bpmn:text>Leilão</bpmn:text>
    </bpmn:textAnnotation>
    <bpmn:association id="Association_1oyxrsb" sourceRef="Flow_19plbaz" targetRef="TextAnnotation_17584va" />
    <bpmn:textAnnotation id="TextAnnotation_0u50c2o">
      <bpmn:text>Compra direta</bpmn:text>
    </bpmn:textAnnotation>
    <bpmn:association id="Association_01tu8vr" sourceRef="Flow_06gtxfj" targetRef="TextAnnotation_0u50c2o" />
    <bpmn:textAnnotation id="TextAnnotation_03jiiih">
      <bpmn:text>Novo lote</bpmn:text>
    </bpmn:textAnnotation>
    <bpmn:association id="Association_08ka0bm" sourceRef="Flow_1d3wt2s" targetRef="TextAnnotation_03jiiih" />
    <bpmn:textAnnotation id="TextAnnotation_0ndl1st">
      <bpmn:text>Lote existente</bpmn:text>
    </bpmn:textAnnotation>
    <bpmn:association id="Association_0r67nwp" sourceRef="Flow_1xaeyg4" targetRef="TextAnnotation_0ndl1st" />
    <bpmn:textAnnotation id="TextAnnotation_16yrn0m">
      <bpmn:text>Descartar</bpmn:text>
    </bpmn:textAnnotation>
    <bpmn:association id="Association_0e0e803" sourceRef="Flow_1rt5bfh" targetRef="TextAnnotation_16yrn0m" />
    <bpmn:textAnnotation id="TextAnnotation_10m28bo">
      <bpmn:text>Detalhes preenchidos</bpmn:text>
    </bpmn:textAnnotation>
    <bpmn:association id="Association_1r8kovs" sourceRef="Flow_0qgdkl4" targetRef="TextAnnotation_10m28bo" />
    <bpmn:textAnnotation id="TextAnnotation_0e9nx5p">
      <bpmn:text>Detalhes incompletos</bpmn:text>
    </bpmn:textAnnotation>
    <bpmn:association id="Association_0tfzfuv" sourceRef="Flow_1cezeva" targetRef="TextAnnotation_0e9nx5p" />
  </bpmn:process>
  <bpmndi:BPMNDiagram id="BPMNDiagram_1">
    <bpmndi:BPMNPlane id="BPMNPlane_1" bpmnElement="Collaboration_111keer">
      <bpmndi:BPMNShape id="Participant_0mkx5e2_di" bpmnElement="Participant_0mkx5e2" isHorizontal="true">
        <dc:Bounds x="150" y="80" width="1668" height="700" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Lane_05tmfu3_di" bpmnElement="Lane_05tmfu3" isHorizontal="true">
        <dc:Bounds x="180" y="80" width="1638" height="700" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="TextAnnotation_17584va_di" bpmnElement="TextAnnotation_17584va">
        <dc:Bounds x="690" y="280" width="99.99202297383536" height="29.993618379068284" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="TextAnnotation_0u50c2o_di" bpmnElement="TextAnnotation_0u50c2o">
        <dc:Bounds x="710" y="600" width="99.99202297383536" height="29.993618379068284" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="TextAnnotation_03jiiih_di" bpmnElement="TextAnnotation_03jiiih">
        <dc:Bounds x="900" y="150" width="99.99202297383536" height="29.993618379068284" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="TextAnnotation_0ndl1st_di" bpmnElement="TextAnnotation_0ndl1st">
        <dc:Bounds x="1043" y="395" width="99.99202297383536" height="29.993618379068284" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="TextAnnotation_16yrn0m_di" bpmnElement="TextAnnotation_16yrn0m">
        <dc:Bounds x="1500" y="570" width="99.99202297383536" height="29.993618379068284" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="TextAnnotation_10m28bo_di" bpmnElement="TextAnnotation_10m28bo">
        <dc:Bounds x="1383" y="390" width="99.99202297383536" height="40.8423739629866" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="TextAnnotation_0e9nx5p_di" bpmnElement="TextAnnotation_0e9nx5p">
        <dc:Bounds x="1384" y="690" width="97" height="41" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="_BPMNShape_StartEvent_2" bpmnElement="StartEvent_1">
        <dc:Bounds x="212" y="422" width="36" height="36" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="164" y="145" width="12" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1wx6ffr_di" bpmnElement="Activity_0vdzca6">
        <dc:Bounds x="300" y="400" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_02v1p5q_di" bpmnElement="Activity_11m3g9g">
        <dc:Bounds x="480" y="400" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_0rg37q4_di" bpmnElement="Gateway_0rg37q4" isMarkerVisible="true">
        <dc:Bounds x="665" y="415" width="50" height="50" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_05jngkn_di" bpmnElement="Gateway_05jngkn" isMarkerVisible="true">
        <dc:Bounds x="995" y="325" width="50" height="50" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0qvzmkq_di" bpmnElement="Activity_0v2womw">
        <dc:Bounds x="800" y="310" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_1byvnuk_di" bpmnElement="Gateway_1byvnuk" isMarkerVisible="true">
        <dc:Bounds x="1395" y="525" width="50" height="50" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_1l7ify3_di" bpmnElement="Event_1l7ify3">
        <dc:Bounds x="1682" y="642" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0uqoejx_di" bpmnElement="Activity_1t4e1ln">
        <dc:Bounds x="1510" y="420" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1grnekc_di" bpmnElement="Activity_0gmykdh">
        <dc:Bounds x="1510" y="620" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_05v77ir_di" bpmnElement="Event_05v77ir">
        <dc:Bounds x="1622" y="532" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_16meh3y_di" bpmnElement="Activity_0w3jhxx">
        <dc:Bounds x="1140" y="170" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_11h704m_di" bpmnElement="Activity_01932vz">
        <dc:Bounds x="1140" y="270" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNEdge id="Association_1oyxrsb_di" bpmnElement="Association_1oyxrsb">
        <di:waypoint x="713" y="350" />
        <di:waypoint x="737" y="280" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Association_01tu8vr_di" bpmnElement="Association_01tu8vr">
        <di:waypoint x="866" y="550" />
        <di:waypoint x="766" y="600" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Association_08ka0bm_di" bpmnElement="Association_08ka0bm">
        <di:waypoint x="1023" y="210" />
        <di:waypoint x="957" y="150" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Association_0r67nwp_di" bpmnElement="Association_0r67nwp">
        <di:waypoint x="1093" y="331" />
        <di:waypoint x="1093" y="395" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Association_0e0e803_di" bpmnElement="Association_0e0e803">
        <di:waypoint x="1533.5" y="550" />
        <di:waypoint x="1549" y="570" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Association_1r8kovs_di" bpmnElement="Association_1r8kovs">
        <di:waypoint x="1432.5" y="460" />
        <di:waypoint x="1433" y="390" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Association_0tfzfuv_di" bpmnElement="Association_0tfzfuv">
        <di:waypoint x="1422.5" y="660" />
        <di:waypoint x="1431" y="690" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0uugwqr_di" bpmnElement="Flow_0uugwqr">
        <di:waypoint x="248" y="440" />
        <di:waypoint x="300" y="440" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0tnse4q_di" bpmnElement="Flow_0tnse4q">
        <di:waypoint x="400" y="440" />
        <di:waypoint x="480" y="440" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0dl6cef_di" bpmnElement="Flow_0dl6cef">
        <di:waypoint x="580" y="440" />
        <di:waypoint x="665" y="440" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_19plbaz_di" bpmnElement="Flow_19plbaz">
        <di:waypoint x="690" y="415" />
        <di:waypoint x="690" y="350" />
        <di:waypoint x="800" y="350" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_021e3gl_di" bpmnElement="Flow_021e3gl">
        <di:waypoint x="900" y="350" />
        <di:waypoint x="995" y="350" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_06gtxfj_di" bpmnElement="Flow_06gtxfj">
        <di:waypoint x="690" y="465" />
        <di:waypoint x="690" y="550" />
        <di:waypoint x="1395" y="550" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1d3wt2s_di" bpmnElement="Flow_1d3wt2s">
        <di:waypoint x="1020" y="325" />
        <di:waypoint x="1020" y="210" />
        <di:waypoint x="1140" y="210" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1xaeyg4_di" bpmnElement="Flow_1xaeyg4">
        <di:waypoint x="1045" y="350" />
        <di:waypoint x="1093" y="350" />
        <di:waypoint x="1093" y="310" />
        <di:waypoint x="1140" y="310" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0qgdkl4_di" bpmnElement="Flow_0qgdkl4">
        <di:waypoint x="1420" y="525" />
        <di:waypoint x="1420" y="460" />
        <di:waypoint x="1510" y="460" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="1269" y="280" width="61" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1cezeva_di" bpmnElement="Flow_1cezeva">
        <di:waypoint x="1420" y="575" />
        <di:waypoint x="1420" y="660" />
        <di:waypoint x="1510" y="660" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="1270" y="405" width="60" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1rt5bfh_di" bpmnElement="Flow_1rt5bfh">
        <di:waypoint x="1445" y="550" />
        <di:waypoint x="1622" y="550" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1nj6hz6_di" bpmnElement="Flow_1nj6hz6">
        <di:waypoint x="1610" y="660" />
        <di:waypoint x="1682" y="660" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_12awwmo_di" bpmnElement="Flow_12awwmo">
        <di:waypoint x="1240" y="210" />
        <di:waypoint x="1320" y="210" />
        <di:waypoint x="1320" y="550" />
        <di:waypoint x="1395" y="550" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_155qcvf_di" bpmnElement="Flow_155qcvf">
        <di:waypoint x="1240" y="310" />
        <di:waypoint x="1320" y="310" />
        <di:waypoint x="1320" y="550" />
        <di:waypoint x="1395" y="550" />
      </bpmndi:BPMNEdge>
    </bpmndi:BPMNPlane>
  </bpmndi:BPMNDiagram>
</bpmn:definitions>
```

#### Detalhamento das atividades

Os tipos de dados a serem utilizados são:

* **Área de texto** - Campo texto de múltiplas linhas
* **Caixa de texto** - campo texto de uma linha
* **Número** - campo numérico
* **Data** - campo do tipo data (dd-mm-aaaa)
* **Hora** - campo do tipo hora (hh:mm:ss)
* **Data e Hora** - campo do tipo data e hora (dd-mm-aaaa, hh:mm:ss)
* **Imagem** - campo - contendo uma imagem
* **Seleção única** - campo com várias opções de valores que são mutuamente exclusivos (tradicional radio button ou combobox)
* **Seleção múltipla** - campo com várias opções que podem ser selecionadas mutuamente (tradicional checkbox ou listbox)
* **Arquivo** - campo de upload de documento
* **Link** - campo que armazena uma URL
* **Tabela** - campo formado por uma matriz de valores

Atividade 1: Iniciar o Processo de Listagem de Minerais

 
| Campo | Tipo | Restrições | Valor padrão |
| ----------------- | ------------------ | -------------- | ----------------- |
| Tipo de Listagem | Seleção Única | | |
| Data de Início | Data | Data atual | Data atual |

 
| Comandos | Destino | Tipo |
| --------------------- | -------------------------------- | ----------------- |
| Criar Listagem | Atividade 2: Criar Listagem | Default |

 
Atividade 2: Criar Listagem

 
| Campo | Tipo | Restrições | Valor padrão |
| ------------------- | ----------------- | -------------- | ----------------- |
| Nome do Mineral | Caixa de Texto | - | - |
| Descrição | Área de Texto | - | - |
| Tipo de Listagem | Seleção Única | - | - |
| Preço Inicial | Número | Valor mínimo: 0| - |
| Quantidade Disponível | Número | Valor mínimo: 1| - |

 
| Comandos | Destino | Tipo |
| -------------------------- | -------------------------------------- | ----------------- |
| Listar para Leilão | Atividade 3: Listar para Leilão | Default |
| Listar para Venda Direta | Atividade 7: Listar para Venda Direta | Default |

 
Atividade 3: Listar para Leilão

 
| Campo | Tipo | Restrições | Valor padrão |
| ------------------- | ----------------- | -------------- | ----------------- |
| Valor de Lance Inicial | Número | Valor mínimo: 0| - |
| Data de Término do Leilão | Data e Hora | Data e hora futura | - |

 
| Comandos | Destino | Tipo |
| -------------------------- | -------------------------------------- | ----------------- |
| Confirmar Listagem no Leilão | Atividade 4: Confirmar Listagem no Leilão | Default |

 
Atividade 4: Confirmar Listagem no Leilão

 
| Campo | Tipo | Restrições | Valor padrão |
| ------------------- | ----------------- | -------------- | ----------------- |
| Detalhes da Listagem | Tabela | - | - |

 
Atividade 5: Listar para Venda Direta

 
| Campo | Tipo | Restrições | Valor padrão |
| ------------------- | ----------------- | -------------- | ----------------- |
| Preço de Venda | Número | Valor mínimo: 0| - |

 
| Comandos | Destino | Tipo |
| -------------------------- | -------------------------------------- | ----------------- |
| Confirmar Listagem Direta | Atividade 6: Confirmar Listagem Direta | Default |

 
Atividade 6: Confirmar Listagem Direta

 
| Campo | Tipo | Restrições | Valor padrão |
| ------------------- | ----------------- | -------------- | ----------------- |
| Detalhes da Listagem Direta | Tabela | - | - |

 
| Comandos | Destino | Tipo |
| -------------------------- | -------------------------------------- | ----------------- |
| Finalizar Listagem Direta | Atividade 7: Finalizar Listagem Direta | Default |

 
Atividade 7: Finalizar Listagem Direta

 
| Campo | Tipo | Restrições | Valor padrão |
| ------------------- | ----------------- | -------------- | ----------------- |
| Valor do Mineral | Número | - | - |

