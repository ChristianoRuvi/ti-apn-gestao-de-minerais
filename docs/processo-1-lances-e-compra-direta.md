### 3.3.1 Processo 1 – Lances e Compras Diretas

Apresente aqui o nome e as oportunidades de melhorias para o processo 1. 
Em seguida, apresente o modelo do processo 1, descrito no padrão BPMN.

```bpmn
<?xml version="1.0" encoding="UTF-8"?>
<bpmn:definitions xmlns:bpmn="http://www.omg.org/spec/BPMN/20100524/MODEL" xmlns:bpmndi="http://www.omg.org/spec/BPMN/20100524/DI" xmlns:dc="http://www.omg.org/spec/DD/20100524/DC" xmlns:di="http://www.omg.org/spec/DD/20100524/DI" xmlns:color="http://www.omg.org/spec/BPMN/non-normative/color/1.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:modeler="http://camunda.org/schema/modeler/1.0" id="Definitions_1c9t4uj" targetNamespace="http://bpmn.io/schema/bpmn" exporter="Camunda Modeler" exporterVersion="5.15.0" modeler:executionPlatform="Camunda Cloud" modeler:executionPlatformVersion="8.2.0">
  <bpmn:collaboration id="Collaboration_1kcd61k">
    <bpmn:participant id="Participant_1nvxizg" name="Lances e compras diretas" processRef="Process_1aois8h" />
  </bpmn:collaboration>
  <bpmn:process id="Process_1aois8h" isExecutable="true">
    <bpmn:laneSet id="LaneSet_0d2e9by" />
    <bpmn:startEvent id="StartEvent_1">
      <bpmn:outgoing>Flow_19umwci</bpmn:outgoing>
    </bpmn:startEvent>
    <bpmn:userTask id="Activity_07envfk" name="Buscar o mineral">
      <bpmn:incoming>Flow_19umwci</bpmn:incoming>
      <bpmn:incoming>Flow_02ytm10</bpmn:incoming>
      <bpmn:outgoing>Flow_1jyjvh9</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:exclusiveGateway id="Gateway_0f5jd9x">
      <bpmn:incoming>Flow_01lr78b</bpmn:incoming>
      <bpmn:outgoing>Flow_071rh36</bpmn:outgoing>
      <bpmn:outgoing>Flow_13lxwun</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:task id="Activity_029zewt" name="Participação do leilão">
      <bpmn:incoming>Flow_1vnc7gt</bpmn:incoming>
      <bpmn:outgoing>Flow_1uaoq5t</bpmn:outgoing>
    </bpmn:task>
    <bpmn:task id="Activity_05x4yc9" name="Dar lance">
      <bpmn:incoming>Flow_1uaoq5t</bpmn:incoming>
      <bpmn:outgoing>Flow_1fukhj2</bpmn:outgoing>
    </bpmn:task>
    <bpmn:exclusiveGateway id="Gateway_11arssd">
      <bpmn:incoming>Flow_1jd7wir</bpmn:incoming>
      <bpmn:outgoing>Flow_19oozc1</bpmn:outgoing>
      <bpmn:outgoing>Flow_1hbqx09</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:task id="Activity_0p6nnmc" name="Escolha forma de pagamento">
      <bpmn:incoming>Flow_1hbqx09</bpmn:incoming>
      <bpmn:outgoing>Flow_11lh8um</bpmn:outgoing>
    </bpmn:task>
    <bpmn:userTask id="Activity_116eb0m" name="Faça o pagamento">
      <bpmn:incoming>Flow_11lh8um</bpmn:incoming>
      <bpmn:outgoing>Flow_0f0a8qb</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:task id="Activity_1wwvqeo" name="Escolha forma de pagamento">
      <bpmn:incoming>Flow_13lxwun</bpmn:incoming>
      <bpmn:outgoing>Flow_13jlfix</bpmn:outgoing>
    </bpmn:task>
    <bpmn:userTask id="Activity_0lcp96f" name="Faça o pagamento">
      <bpmn:incoming>Flow_13jlfix</bpmn:incoming>
      <bpmn:outgoing>Flow_1hazw25</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:sequenceFlow id="Flow_19umwci" sourceRef="StartEvent_1" targetRef="Activity_07envfk" />
    <bpmn:sequenceFlow id="Flow_1jyjvh9" sourceRef="Activity_07envfk" targetRef="Activity_1r1323j" />
    <bpmn:sequenceFlow id="Flow_01lr78b" sourceRef="Activity_1d0w2gu" targetRef="Gateway_0f5jd9x" />
    <bpmn:sequenceFlow id="Flow_071rh36" name="Opção do leilão" sourceRef="Gateway_0f5jd9x" targetRef="Activity_05mg5v8">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'yes'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:sequenceFlow id="Flow_13lxwun" name="Opção de compra direta" sourceRef="Gateway_0f5jd9x" targetRef="Activity_1wwvqeo">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'yes'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:sequenceFlow id="Flow_1rzkf0d" sourceRef="Activity_05mg5v8" targetRef="Activity_09vu229" />
    <bpmn:sequenceFlow id="Flow_1vnc7gt" sourceRef="Activity_09vu229" targetRef="Activity_029zewt" />
    <bpmn:sequenceFlow id="Flow_1uaoq5t" sourceRef="Activity_029zewt" targetRef="Activity_05x4yc9" />
    <bpmn:sequenceFlow id="Flow_1fukhj2" sourceRef="Activity_05x4yc9" targetRef="Activity_1hahi8m" />
    <bpmn:sequenceFlow id="Flow_1jd7wir" sourceRef="Activity_1hahi8m" targetRef="Gateway_11arssd" />
    <bpmn:sequenceFlow id="Flow_19oozc1" name="Não foi o maior lançe" sourceRef="Gateway_11arssd" targetRef="Event_13wkcdg">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'yes'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:sequenceFlow id="Flow_1hbqx09" name="Foi o maior lance" sourceRef="Gateway_11arssd" targetRef="Activity_0p6nnmc">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'yes'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:sequenceFlow id="Flow_11lh8um" sourceRef="Activity_0p6nnmc" targetRef="Activity_116eb0m" />
    <bpmn:sequenceFlow id="Flow_0f0a8qb" sourceRef="Activity_116eb0m" targetRef="Activity_1prirvn" />
    <bpmn:sequenceFlow id="Flow_13jlfix" sourceRef="Activity_1wwvqeo" targetRef="Activity_0lcp96f" />
    <bpmn:sequenceFlow id="Flow_1hazw25" sourceRef="Activity_0lcp96f" targetRef="Activity_060no5w" />
    <bpmn:sequenceFlow id="Flow_12s7na1" sourceRef="Activity_060no5w" targetRef="Activity_0uj73k6" />
    <bpmn:sequenceFlow id="Flow_0v251j5" sourceRef="Activity_1prirvn" targetRef="Activity_0d01tma" />
    <bpmn:task id="Activity_060no5w" name="Pagamento aprovado">
      <bpmn:incoming>Flow_1hazw25</bpmn:incoming>
      <bpmn:outgoing>Flow_12s7na1</bpmn:outgoing>
    </bpmn:task>
    <bpmn:task id="Activity_0uj73k6" name="Enviar recibo e confirmação de compra">
      <bpmn:incoming>Flow_12s7na1</bpmn:incoming>
    </bpmn:task>
    <bpmn:task id="Activity_09vu229" name="Validação do registro">
      <bpmn:incoming>Flow_1rzkf0d</bpmn:incoming>
      <bpmn:outgoing>Flow_1vnc7gt</bpmn:outgoing>
    </bpmn:task>
    <bpmn:task id="Activity_1hahi8m" name="Leilão finalizado">
      <bpmn:incoming>Flow_1fukhj2</bpmn:incoming>
      <bpmn:outgoing>Flow_1jd7wir</bpmn:outgoing>
    </bpmn:task>
    <bpmn:task id="Activity_1prirvn" name="Pagamento aprovado">
      <bpmn:incoming>Flow_0f0a8qb</bpmn:incoming>
      <bpmn:outgoing>Flow_0v251j5</bpmn:outgoing>
    </bpmn:task>
    <bpmn:task id="Activity_0d01tma" name="Enviar recibo e confirmação de compra">
      <bpmn:incoming>Flow_0v251j5</bpmn:incoming>
    </bpmn:task>
    <bpmn:task id="Activity_1r1323j" name="Verificar se o mineral esta disponivel">
      <bpmn:incoming>Flow_1jyjvh9</bpmn:incoming>
      <bpmn:outgoing>Flow_1q9pdjh</bpmn:outgoing>
    </bpmn:task>
    <bpmn:sequenceFlow id="Flow_1q9pdjh" sourceRef="Activity_1r1323j" targetRef="Gateway_1i9z25w" />
    <bpmn:sequenceFlow id="Flow_1ysi6ld" name="Mineral disponivel" sourceRef="Gateway_1i9z25w" targetRef="Activity_1d0w2gu">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'Mineral disponivel'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:sequenceFlow id="Flow_02ytm10" name="Mineral não disponivel" sourceRef="Gateway_1i9z25w" targetRef="Activity_07envfk">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'Mineral não disponivel'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:exclusiveGateway id="Gateway_1i9z25w">
      <bpmn:incoming>Flow_1q9pdjh</bpmn:incoming>
      <bpmn:outgoing>Flow_1ysi6ld</bpmn:outgoing>
      <bpmn:outgoing>Flow_02ytm10</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:userTask id="Activity_1d0w2gu" name="Escolher entre leilão ou compra direta">
      <bpmn:incoming>Flow_1ysi6ld</bpmn:incoming>
      <bpmn:outgoing>Flow_01lr78b</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:userTask id="Activity_05mg5v8" name="Faça o registro com nome, numero e         e-mail.">
      <bpmn:incoming>Flow_071rh36</bpmn:incoming>
      <bpmn:outgoing>Flow_1rzkf0d</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:endEvent id="Event_13wkcdg">
      <bpmn:incoming>Flow_19oozc1</bpmn:incoming>
    </bpmn:endEvent>
  </bpmn:process>
  <bpmndi:BPMNDiagram id="BPMNDiagram_1">
    <bpmndi:BPMNPlane id="BPMNPlane_1" bpmnElement="Collaboration_1kcd61k">
      <bpmndi:BPMNShape id="Participant_1nvxizg_di" bpmnElement="Participant_1nvxizg" isHorizontal="true">
        <dc:Bounds x="160" y="80" width="2650" height="580" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="_BPMNShape_StartEvent_2" bpmnElement="StartEvent_1">
        <dc:Bounds x="193" y="372" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_07envfk_di" bpmnElement="Activity_07envfk">
        <dc:Bounds x="281" y="350" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_0f5jd9x_di" bpmnElement="Gateway_0f5jd9x" isMarkerVisible="true">
        <dc:Bounds x="816" y="375" width="50" height="50" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_029zewt_di" bpmnElement="Activity_029zewt">
        <dc:Bounds x="1380" y="220" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_05x4yc9_di" bpmnElement="Activity_05x4yc9">
        <dc:Bounds x="1520" y="220" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_11arssd_di" bpmnElement="Gateway_11arssd" isMarkerVisible="true">
        <dc:Bounds x="1855" y="255" width="50" height="50" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0p6nnmc_di" bpmnElement="Activity_0p6nnmc">
        <dc:Bounds x="2110" y="120" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_034lx8u_di" bpmnElement="Activity_116eb0m">
        <dc:Bounds x="2300" y="130" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1wwvqeo_di" bpmnElement="Activity_1wwvqeo">
        <dc:Bounds x="1090" y="460" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1m129fs_di" bpmnElement="Activity_0lcp96f">
        <dc:Bounds x="1290" y="460" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1m8ao1g_di" bpmnElement="Activity_060no5w">
        <dc:Bounds x="1430" y="460" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_15xac70_di" bpmnElement="Activity_0uj73k6">
        <dc:Bounds x="1590" y="460" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1p7v0xo_di" bpmnElement="Activity_09vu229">
        <dc:Bounds x="1240" y="210" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_06806xf_di" bpmnElement="Activity_1hahi8m">
        <dc:Bounds x="1670" y="220" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1ar8mi0_di" bpmnElement="Activity_1prirvn">
        <dc:Bounds x="2440" y="130" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0gmi3m8_di" bpmnElement="Activity_0d01tma">
        <dc:Bounds x="2610" y="130" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1ex5i8m_di" bpmnElement="Activity_1r1323j">
        <dc:Bounds x="421" y="350" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_0g3bexd_di" bpmnElement="Gateway_1i9z25w" isMarkerVisible="true">
        <dc:Bounds x="548" y="375" width="50" height="50" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1d0w2gu_di" bpmnElement="Activity_1d0w2gu">
        <dc:Bounds x="670" y="500" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_17oi0ci_di" bpmnElement="Activity_05mg5v8">
        <dc:Bounds x="1070" y="210" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_1upvtf7_di" bpmnElement="Event_13wkcdg">
        <dc:Bounds x="1962" y="422" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNEdge id="Flow_19umwci_di" bpmnElement="Flow_19umwci">
        <di:waypoint x="229" y="390" />
        <di:waypoint x="281" y="390" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1jyjvh9_di" bpmnElement="Flow_1jyjvh9">
        <di:waypoint x="381" y="390" />
        <di:waypoint x="421" y="390" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_01lr78b_di" bpmnElement="Flow_01lr78b">
        <di:waypoint x="720" y="500" />
        <di:waypoint x="720" y="400" />
        <di:waypoint x="816" y="400" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_071rh36_di" bpmnElement="Flow_071rh36">
        <di:waypoint x="841" y="375" />
        <di:waypoint x="841" y="250" />
        <di:waypoint x="1070" y="250" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="891" y="253" width="77" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_13lxwun_di" bpmnElement="Flow_13lxwun">
        <di:waypoint x="841" y="425" />
        <di:waypoint x="841" y="500" />
        <di:waypoint x="1090" y="500" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="896" y="466" width="88" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1rzkf0d_di" bpmnElement="Flow_1rzkf0d">
        <di:waypoint x="1170" y="250" />
        <di:waypoint x="1205" y="250" />
        <di:waypoint x="1205" y="270" />
        <di:waypoint x="1240" y="270" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1vnc7gt_di" bpmnElement="Flow_1vnc7gt">
        <di:waypoint x="1340" y="250" />
        <di:waypoint x="1360" y="250" />
        <di:waypoint x="1360" y="260" />
        <di:waypoint x="1380" y="260" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1uaoq5t_di" bpmnElement="Flow_1uaoq5t">
        <di:waypoint x="1480" y="260" />
        <di:waypoint x="1520" y="260" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1fukhj2_di" bpmnElement="Flow_1fukhj2">
        <di:waypoint x="1620" y="260" />
        <di:waypoint x="1670" y="260" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1jd7wir_di" bpmnElement="Flow_1jd7wir">
        <di:waypoint x="1770" y="260" />
        <di:waypoint x="1813" y="260" />
        <di:waypoint x="1813" y="280" />
        <di:waypoint x="1855" y="280" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_19oozc1_di" bpmnElement="Flow_19oozc1">
        <di:waypoint x="1880" y="305" />
        <di:waypoint x="1880" y="380" />
        <di:waypoint x="1980" y="380" />
        <di:waypoint x="1980" y="422" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="1902" y="336" width="76" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1hbqx09_di" bpmnElement="Flow_1hbqx09">
        <di:waypoint x="1880" y="255" />
        <di:waypoint x="1880" y="160" />
        <di:waypoint x="2110" y="160" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="1917" y="173" width="85" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_11lh8um_di" bpmnElement="Flow_11lh8um">
        <di:waypoint x="2210" y="160" />
        <di:waypoint x="2255" y="160" />
        <di:waypoint x="2255" y="170" />
        <di:waypoint x="2300" y="170" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0f0a8qb_di" bpmnElement="Flow_0f0a8qb">
        <di:waypoint x="2400" y="170" />
        <di:waypoint x="2440" y="170" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_13jlfix_di" bpmnElement="Flow_13jlfix">
        <di:waypoint x="1190" y="500" />
        <di:waypoint x="1290" y="500" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1hazw25_di" bpmnElement="Flow_1hazw25">
        <di:waypoint x="1390" y="500" />
        <di:waypoint x="1430" y="500" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_12s7na1_di" bpmnElement="Flow_12s7na1">
        <di:waypoint x="1530" y="500" />
        <di:waypoint x="1590" y="500" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0v251j5_di" bpmnElement="Flow_0v251j5">
        <di:waypoint x="2540" y="170" />
        <di:waypoint x="2610" y="170" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1q9pdjh_di" bpmnElement="Flow_1q9pdjh">
        <di:waypoint x="521" y="390" />
        <di:waypoint x="535" y="390" />
        <di:waypoint x="535" y="400" />
        <di:waypoint x="548" y="400" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1ysi6ld_di" bpmnElement="Flow_1ysi6ld">
        <di:waypoint x="573" y="425" />
        <di:waypoint x="573" y="463" />
        <di:waypoint x="551" y="463" />
        <di:waypoint x="551" y="540" />
        <di:waypoint x="670" y="540" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="553" y="523" width="89" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_02ytm10_di" bpmnElement="Flow_02ytm10">
        <di:waypoint x="573" y="375" />
        <di:waypoint x="573" y="280" />
        <di:waypoint x="480" y="280" />
        <di:waypoint x="350" y="350" />
        <bpmndi:BPMNLabel color:color="#0d4372">
          <dc:Bounds x="506" y="246" width="58" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
    </bpmndi:BPMNPlane>
  </bpmndi:BPMNDiagram>
</bpmn:definitions>

```

#### Detalhamento das atividades

Descrever aqui cada uma das propriedades das atividades do processo 1. 
Devem estar relacionadas com o modelo de processo apresentado anteriormente.

Os tipos de dados a serem utilizados são:
**Atividade 1: Iniciar o Processo de Compra de Mineral**

| **Campo**         | **Tipo**           | **Restrições** | **Valor padrão** |
| ----------------- | ------------------ | -------------- | ----------------- |
| Busca de Mineral  | Caixa de Texto     |                |                   |
| Data de Início    | Data               | Data atual     | Data atual        |

| **Comandos**         | **Destino**                      | **Tipo**          |
| --------------------- | -------------------------------- | ----------------- |
| Pesquisar Minerais    | Atividade 2: Pesquisar Minerais   | Default           |
| Comprar Diretamente  | Atividade 9: Compra Direta         | Default           |

**Atividade 2: Pesquisar Minerais Disponíveis**

| **Campo**           | **Tipo**          | **Restrições** | **Valor padrão** |
| ------------------- | ----------------- | -------------- | ----------------- |
| Tipo de Mineral     | Seleção Única     |                |                   |
| Faixa de Preço      | Número            | Valor mínimo: 0|                   |

| **Comandos**               | **Destino**                            | **Tipo**          |
| -------------------------- | -------------------------------------- | ----------------- |
| Selecionar Mineral         | Atividade 3: Selecionar um Mineral     | Default           |

**Atividade 3: Selecionar um Mineral**

| **Campo**              | **Tipo**           | **Restrições** | **Valor padrão** |
| ---------------------- | ------------------ | -------------- | ----------------- |
| Detalhes do Mineral    | Tabela             |                |                   |

| **Comandos**               | **Destino**                              | **Tipo**          |
| -------------------------- | ---------------------------------------- | ----------------- |
| Registrar para o Leilão    | Atividade 4: Registrar para o Leilão      | Default           |

**Atividade 4: Registrar para o Leilão**

| **Campo**              | **Tipo**           | **Restrições** | **Valor padrão** |
| ---------------------- | ------------------ | -------------- | ----------------- |
| Nome Completo          | Caixa de Texto     |                |                   |
| Endereço de E-mail    | Caixa de Texto     | Formato de e-mail válido |   |
| Número de Telefone    | Número             | Formato de número válido |   |

| **Comandos**               | **Destino**                              | **Tipo**          |
| -------------------------- | ---------------------------------------- | ----------------- |
| Enviar Registro           | Atividade 5: Participar do Leilão         | Default           |

**Atividade 5: Participar do Leilão**

| **Campo**              | **Tipo**           | **Restrições** | **Valor padrão** |
| ---------------------- | ------------------ | -------------- | ----------------- |
| Valor do Lance         | Número             | Valor mínimo: 0| 0                 |

| **Comandos**               | **Destino**                              | **Tipo**          |
| -------------------------- | ---------------------------------------- | ----------------- |
| Fazer Lance               | Atividade 6: Participação no Leilão       | Default           |

**Atividade 6: Participação no Leilão**

| **Campo**              | **Tipo**           | **Restrições** | **Valor padrão** |
| ---------------------- | ------------------ | -------------- | ----------------- |
| Lances Feitos           | Tabela             |                |                   |

| **Comandos**               | **Destino**                              | **Tipo**          |
| -------------------------- | ---------------------------------------- | ----------------- |
| Finalizar Leilão          | Atividade 7: Finalizar Leilão            | Default           |

**Atividade 7: Finalizar Leilão**

| **Campo**              | **Tipo**           | **Restrições** | **Valor padrão** |
| ---------------------- | ------------------ | -------------- | ----------------- |
| Valor do Mineral        | Número             |                |                   |

| **Comandos**               | **Destino**                              | **Tipo**          |
| -------------------------- | ---------------------------------------- | ----------------- |
| Pagar pelo Mineral        | Atividade 8: Pagar pelo Mineral          | Default           |

**Atividade 8: Pagar pelo Mineral**

| **Campo**              | **Tipo**           | **Restrições** | **Valor padrão** |
| ---------------------- | ------------------ | -------------- | ----------------- |
| Método de Pagamento      | Seleção Única      |                |                   |

| **Comandos**               | **Destino**                              | **Tipo**          |
| -------------------------- | ---------------------------------------- | ----------------- |
| Confirmar Pagamento        | Atividade 10: Concluir o Processo   | Default           |

**Atividade 9: Compra Direta por Valor Específico**

| **Campo**              | **Tipo**           | **Restrições** | **Valor padrão** |
| ---------------------- | ------------------ | -------------- | ----------------- |
| Valor da Compra        | Número             | Valor mínimo: 0| 0                 |

| **Comandos**               | **Destino**                              | **Tipo**          |
| -------------------------- | ---------------------------------------- | ----------------- |
| Confirmar Compra          | Atividade 10: Concluir o Processo          | Default           |
**Atividade 10: Concluir o Processo**
