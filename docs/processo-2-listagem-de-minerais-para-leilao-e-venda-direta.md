### 3.3.2 Processo 2 – NOME DO PROCESSO

Apresente aqui o nome e as oportunidades de melhorias para o processo 2. 
Em seguida, apresente o modelo do processo 2, descrito no padrão BPMN.

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
        <bpmn:flowNodeRef>Gateway_1byvnuk</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Event_1l7ify3</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1t4e1ln</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_0gmykdh</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_11m3g9g</bpmn:flowNodeRef>
      </bpmn:lane>
      <bpmn:lane id="Lane_032w1fr" name="Cliente">
        <bpmn:flowNodeRef>Activity_1sjv2bg</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Gateway_1yfthj7</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_0e80xso</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1cou1om</bpmn:flowNodeRef>
      </bpmn:lane>
    </bpmn:laneSet>
    <bpmn:startEvent id="StartEvent_1">
      <bpmn:outgoing>Flow_0uugwqr</bpmn:outgoing>
    </bpmn:startEvent>
    <bpmn:userTask id="Activity_0vdzca6" name="Criar nova listagem">
      <bpmn:incoming>Flow_0uugwqr</bpmn:incoming>
      <bpmn:outgoing>Flow_0tnse4q</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:exclusiveGateway id="Gateway_1byvnuk">
      <bpmn:incoming>Flow_1svokii</bpmn:incoming>
      <bpmn:outgoing>Flow_0qgdkl4</bpmn:outgoing>
      <bpmn:outgoing>Flow_1cezeva</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:sequenceFlow id="Flow_0uugwqr" sourceRef="StartEvent_1" targetRef="Activity_0vdzca6" />
    <bpmn:sequenceFlow id="Flow_0tnse4q" sourceRef="Activity_0vdzca6" targetRef="Activity_11m3g9g" />
    <bpmn:sequenceFlow id="Flow_1svokii" sourceRef="Activity_11m3g9g" targetRef="Gateway_1byvnuk" />
    <bpmn:sequenceFlow id="Flow_0qgdkl4" name="Detalhes preenchidos" sourceRef="Gateway_1byvnuk" targetRef="Activity_1t4e1ln">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'Dados Preenchidos'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:sequenceFlow id="Flow_1cezeva" name="Detalhes incompletos" sourceRef="Gateway_1byvnuk" targetRef="Activity_0gmykdh">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'Dados Incompletos'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:endEvent id="Event_1l7ify3">
      <bpmn:incoming>Flow_1nj6hz6</bpmn:incoming>
    </bpmn:endEvent>
    <bpmn:sequenceFlow id="Flow_1nj6hz6" sourceRef="Activity_0gmykdh" targetRef="Event_1l7ify3" />
    <bpmn:serviceTask id="Activity_1t4e1ln" name="Publicar item">
      <bpmn:incoming>Flow_0qgdkl4</bpmn:incoming>
      <bpmn:outgoing>Flow_1ib9exs</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:serviceTask id="Activity_0gmykdh" name="Salvar item como rascunho">
      <bpmn:incoming>Flow_1cezeva</bpmn:incoming>
      <bpmn:outgoing>Flow_1nj6hz6</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:userTask id="Activity_11m3g9g" name="Adicionar detalhes do item">
      <bpmn:incoming>Flow_0tnse4q</bpmn:incoming>
      <bpmn:outgoing>Flow_1svokii</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:sequenceFlow id="Flow_1ib9exs" sourceRef="Activity_1t4e1ln" targetRef="Activity_1sjv2bg" />
    <bpmn:userTask id="Activity_1sjv2bg" name="Visualizar item">
      <bpmn:incoming>Flow_1ib9exs</bpmn:incoming>
      <bpmn:outgoing>Flow_16bc5hc</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:sequenceFlow id="Flow_16bc5hc" sourceRef="Activity_1sjv2bg" targetRef="Gateway_1yfthj7" />
    <bpmn:exclusiveGateway id="Gateway_1yfthj7">
      <bpmn:incoming>Flow_16bc5hc</bpmn:incoming>
      <bpmn:outgoing>Flow_18dafby</bpmn:outgoing>
      <bpmn:outgoing>Flow_0lr4vqd</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:sequenceFlow id="Flow_18dafby" sourceRef="Gateway_1yfthj7" targetRef="Activity_1cou1om" />
    <bpmn:sequenceFlow id="Flow_0lr4vqd" sourceRef="Gateway_1yfthj7" targetRef="Activity_0e80xso" />
    <bpmn:subProcess id="Activity_0e80xso" name="Compra direta">
      <bpmn:incoming>Flow_0lr4vqd</bpmn:incoming>
    </bpmn:subProcess>
    <bpmn:serviceTask id="Activity_1cou1om" name="Mostrar lance atual">
      <bpmn:incoming>Flow_18dafby</bpmn:incoming>
    </bpmn:serviceTask>
  </bpmn:process>
  <bpmndi:BPMNDiagram id="BPMNDiagram_1">
    <bpmndi:BPMNPlane id="BPMNPlane_1" bpmnElement="Collaboration_111keer">
      <bpmndi:BPMNShape id="Participant_0mkx5e2_di" bpmnElement="Participant_0mkx5e2" isHorizontal="true">
        <dc:Bounds x="150" y="80" width="960" height="680" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Lane_05tmfu3_di" bpmnElement="Lane_05tmfu3" isHorizontal="true">
        <dc:Bounds x="180" y="80" width="930" height="320" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Lane_032w1fr_di" bpmnElement="Lane_032w1fr" isHorizontal="true">
        <dc:Bounds x="180" y="400" width="930" height="360" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="_BPMNShape_StartEvent_2" bpmnElement="StartEvent_1">
        <dc:Bounds x="212" y="212" width="36" height="36" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="164" y="145" width="12" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1wx6ffr_di" bpmnElement="Activity_0vdzca6">
        <dc:Bounds x="300" y="190" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_1byvnuk_di" bpmnElement="Gateway_1byvnuk" isMarkerVisible="true">
        <dc:Bounds x="625" y="205" width="50" height="50" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_1l7ify3_di" bpmnElement="Event_1l7ify3">
        <dc:Bounds x="912" y="322" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0uqoejx_di" bpmnElement="Activity_1t4e1ln">
        <dc:Bounds x="740" y="100" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1grnekc_di" bpmnElement="Activity_0gmykdh">
        <dc:Bounds x="740" y="300" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_02v1p5q_di" bpmnElement="Activity_11m3g9g">
        <dc:Bounds x="480" y="190" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0hmb64v_di" bpmnElement="Activity_1sjv2bg">
        <dc:Bounds x="220" y="420" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_1yfthj7_di" bpmnElement="Gateway_1yfthj7" isMarkerVisible="true">
        <dc:Bounds x="325" y="525" width="50" height="50" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0inm5os_di" bpmnElement="Activity_1cou1om">
        <dc:Bounds x="480" y="510" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1azxuji_di" bpmnElement="Activity_0e80xso">
        <dc:Bounds x="480" y="620" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNEdge id="Flow_0uugwqr_di" bpmnElement="Flow_0uugwqr">
        <di:waypoint x="248" y="230" />
        <di:waypoint x="300" y="230" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0tnse4q_di" bpmnElement="Flow_0tnse4q">
        <di:waypoint x="400" y="230" />
        <di:waypoint x="480" y="230" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1svokii_di" bpmnElement="Flow_1svokii">
        <di:waypoint x="580" y="230" />
        <di:waypoint x="625" y="230" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0qgdkl4_di" bpmnElement="Flow_0qgdkl4">
        <di:waypoint x="650" y="205" />
        <di:waypoint x="650" y="140" />
        <di:waypoint x="740" y="140" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="659" y="170" width="61" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1cezeva_di" bpmnElement="Flow_1cezeva">
        <di:waypoint x="650" y="255" />
        <di:waypoint x="650" y="340" />
        <di:waypoint x="740" y="340" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="660" y="295" width="60" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1nj6hz6_di" bpmnElement="Flow_1nj6hz6">
        <di:waypoint x="840" y="340" />
        <di:waypoint x="912" y="340" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1ib9exs_di" bpmnElement="Flow_1ib9exs">
        <di:waypoint x="840" y="140" />
        <di:waypoint x="970" y="140" />
        <di:waypoint x="970" y="460" />
        <di:waypoint x="320" y="460" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_16bc5hc_di" bpmnElement="Flow_16bc5hc">
        <di:waypoint x="270" y="500" />
        <di:waypoint x="270" y="550" />
        <di:waypoint x="325" y="550" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_18dafby_di" bpmnElement="Flow_18dafby">
        <di:waypoint x="375" y="550" />
        <di:waypoint x="480" y="550" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0lr4vqd_di" bpmnElement="Flow_0lr4vqd">
        <di:waypoint x="350" y="575" />
        <di:waypoint x="350" y="660" />
        <di:waypoint x="480" y="660" />
      </bpmndi:BPMNEdge>
    </bpmndi:BPMNPlane>
  </bpmndi:BPMNDiagram>
  <bpmndi:BPMNDiagram id="BPMNDiagram_1w9lyl3">
    <bpmndi:BPMNPlane id="BPMNPlane_1rdjaml" bpmnElement="Activity_0e80xso" />
  </bpmndi:BPMNDiagram>
</bpmn:definitions>
```

#### Detalhamento das atividades

Descrever aqui cada uma das propriedades das atividades do processo 2. 
Devem estar relacionadas com o modelo de processo apresentado anteriormente.

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

**Nome da atividade 1**

| **Campo**       | **Tipo**         | **Restrições** | **Valor default** |
| ---             | ---              | ---            | ---               |
| [Nome do campo] | [tipo de dados]  |                |                   |
| ***Exemplo:***  |                  |                |                   |
| login           | Caixa de Texto   | formato de e-mail |                |
| senha           | Caixa de Texto   | mínimo de 8 caracteres |           |

| **Comandos**         |  **Destino**                   | **Tipo** |
| ---                  | ---                            | ---               |
| [Nome do botão/link] | Atividade/processo de destino  | (default/cancel/  ) |
| ***Exemplo:***       |                                |                   |
| entrar               | Fim do Processo 1              | default           |
| cadastrar            | Início do proceso de cadastro  |                   |


**Nome da atividade 2**

| **Campo**       | **Tipo**         | **Restrições** | **Valor default** |
| ---             | ---              | ---            | ---               |
| [Nome do campo] | [tipo de dados]  |                |                   |
|                 |                  |                |                   |

| **Comandos**         |  **Destino**                   | **Tipo**          |
| ---                  | ---                            | ---               |
| [Nome do botão/link] | Atividade/processo de destino  | (default/cancel/  ) |
|                      |                                |                   |
