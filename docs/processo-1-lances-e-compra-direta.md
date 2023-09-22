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
    <bpmn:serviceTask id="Activity_1r1323j" name="Verificar se o mineral esta disponivel">
      <bpmn:incoming>Flow_1jyjvh9</bpmn:incoming>
      <bpmn:outgoing>Flow_1q9pdjh</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:serviceTask id="Activity_0uj73k6" name="Enviar recibo e confirmação de compra">
      <bpmn:incoming>Flow_12s7na1</bpmn:incoming>
      <bpmn:outgoing>Flow_0vqppic</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:sequenceFlow id="Flow_1q9pdjh" sourceRef="Activity_1r1323j" targetRef="Gateway_1i9z25w" />
    <bpmn:serviceTask id="Activity_060no5w" name="Pagamento aprovado">
      <bpmn:incoming>Flow_1hazw25</bpmn:incoming>
      <bpmn:outgoing>Flow_12s7na1</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:sequenceFlow id="Flow_12s7na1" sourceRef="Activity_060no5w" targetRef="Activity_0uj73k6" />
    <bpmn:userTask id="Activity_1wwvqeo" name="Escolha forma de pagamento">
      <bpmn:incoming>Flow_13lxwun</bpmn:incoming>
      <bpmn:outgoing>Flow_13jlfix</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:sequenceFlow id="Flow_13jlfix" sourceRef="Activity_1wwvqeo" targetRef="Activity_0lcp96f" />
    <bpmn:endEvent id="Event_13wkcdg">
      <bpmn:incoming>Flow_02dqcmc</bpmn:incoming>
    </bpmn:endEvent>
    <bpmn:receiveTask id="Activity_03cah9k" name="Recebera uma mensagem que seu lance não foi o maior">
      <bpmn:incoming>Flow_16uhnxs</bpmn:incoming>
      <bpmn:outgoing>Flow_02dqcmc</bpmn:outgoing>
    </bpmn:receiveTask>
    <bpmn:sequenceFlow id="Flow_02dqcmc" sourceRef="Activity_03cah9k" targetRef="Event_13wkcdg" />
    <bpmn:intermediateCatchEvent id="Event_1f80boa">
      <bpmn:incoming>Flow_19oozc1</bpmn:incoming>
      <bpmn:outgoing>Flow_16uhnxs</bpmn:outgoing>
      <bpmn:messageEventDefinition id="MessageEventDefinition_0zbnpvh" />
    </bpmn:intermediateCatchEvent>
    <bpmn:sequenceFlow id="Flow_16uhnxs" sourceRef="Event_1f80boa" targetRef="Activity_03cah9k" />
    <bpmn:intermediateThrowEvent id="Event_1xms693">
      <bpmn:incoming>Flow_0vqppic</bpmn:incoming>
      <bpmn:linkEventDefinition id="LinkEventDefinition_10cgj4b" name="" />
    </bpmn:intermediateThrowEvent>
    <bpmn:sequenceFlow id="Flow_0vqppic" sourceRef="Activity_0uj73k6" targetRef="Event_1xms693" />
    <bpmn:userTask id="Activity_1d0w2gu" name="Escolher entre leilão ou compra direta">
      <bpmn:incoming>Flow_1ysi6ld</bpmn:incoming>
      <bpmn:outgoing>Flow_01lr78b</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:sequenceFlow id="Flow_01lr78b" sourceRef="Activity_1d0w2gu" targetRef="Gateway_0f5jd9x" />
    <bpmn:exclusiveGateway id="Gateway_1i9z25w">
      <bpmn:incoming>Flow_1q9pdjh</bpmn:incoming>
      <bpmn:outgoing>Flow_1ysi6ld</bpmn:outgoing>
      <bpmn:outgoing>Flow_02ytm10</bpmn:outgoing>
      <bpmn:outgoing>Flow_11vzu32</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:sequenceFlow id="Flow_1ysi6ld" name="Mineral disponivel" sourceRef="Gateway_1i9z25w" targetRef="Activity_1d0w2gu">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'Mineral disponivel'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:userTask id="Activity_0lcp96f" name="Faça o pagamento">
      <bpmn:incoming>Flow_13jlfix</bpmn:incoming>
      <bpmn:outgoing>Flow_1hazw25</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:sequenceFlow id="Flow_1hazw25" sourceRef="Activity_0lcp96f" targetRef="Activity_060no5w" />
    <bpmn:exclusiveGateway id="Gateway_0f5jd9x">
      <bpmn:incoming>Flow_01lr78b</bpmn:incoming>
      <bpmn:outgoing>Flow_13lxwun</bpmn:outgoing>
      <bpmn:outgoing>Flow_071rh36</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:sequenceFlow id="Flow_13lxwun" name="Opção de compra direta" sourceRef="Gateway_0f5jd9x" targetRef="Activity_1wwvqeo">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'yes'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:userTask id="Activity_07envfk" name="Buscar o mineral">
      <bpmn:incoming>Flow_02ytm10</bpmn:incoming>
      <bpmn:incoming>Flow_19umwci</bpmn:incoming>
      <bpmn:outgoing>Flow_1jyjvh9</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:sequenceFlow id="Flow_1jyjvh9" sourceRef="Activity_07envfk" targetRef="Activity_1r1323j" />
    <bpmn:sequenceFlow id="Flow_02ytm10" name="Mineral não disponivel" sourceRef="Gateway_1i9z25w" targetRef="Activity_07envfk">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'Mineral não disponivel'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:sequenceFlow id="Flow_19umwci" sourceRef="StartEvent_1" targetRef="Activity_07envfk" />
    <bpmn:serviceTask id="Activity_0d01tma" name="Enviar recibo e confirmação de compra">
      <bpmn:incoming>Flow_0v251j5</bpmn:incoming>
      <bpmn:outgoing>Flow_0oj1dyp</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:intermediateThrowEvent id="Event_0ri09ng">
      <bpmn:incoming>Flow_0oj1dyp</bpmn:incoming>
      <bpmn:linkEventDefinition id="LinkEventDefinition_047jyyw" name="" />
    </bpmn:intermediateThrowEvent>
    <bpmn:sequenceFlow id="Flow_0oj1dyp" sourceRef="Activity_0d01tma" targetRef="Event_0ri09ng" />
    <bpmn:serviceTask id="Activity_1prirvn" name="Pagamento aprovado">
      <bpmn:incoming>Flow_0f0a8qb</bpmn:incoming>
      <bpmn:outgoing>Flow_0v251j5</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:sequenceFlow id="Flow_0v251j5" sourceRef="Activity_1prirvn" targetRef="Activity_0d01tma" />
    <bpmn:userTask id="Activity_0p6nnmc" name="Escolha forma de pagamento">
      <bpmn:incoming>Flow_0jq454g</bpmn:incoming>
      <bpmn:outgoing>Flow_11lh8um</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:sequenceFlow id="Flow_11lh8um" sourceRef="Activity_0p6nnmc" targetRef="Activity_116eb0m" />
    <bpmn:userTask id="Activity_05x4yc9" name="Dar lance">
      <bpmn:incoming>Flow_1vnc7gt</bpmn:incoming>
      <bpmn:outgoing>Flow_13u7s76</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:sequenceFlow id="Flow_071rh36" name="Opção do leilão" sourceRef="Gateway_0f5jd9x" targetRef="Activity_05mg5v8">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'yes'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:serviceTask id="Activity_09vu229" name="Validação do registro">
      <bpmn:incoming>Flow_1rzkf0d</bpmn:incoming>
      <bpmn:outgoing>Flow_1vnc7gt</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:sequenceFlow id="Flow_1vnc7gt" sourceRef="Activity_09vu229" targetRef="Activity_05x4yc9" />
    <bpmn:receiveTask id="Activity_1j5z80v" name="Recebera uma mensagem que seu lance foi o maior">
      <bpmn:incoming>Flow_0176wdp</bpmn:incoming>
      <bpmn:outgoing>Flow_0jq454g</bpmn:outgoing>
    </bpmn:receiveTask>
    <bpmn:sequenceFlow id="Flow_0jq454g" sourceRef="Activity_1j5z80v" targetRef="Activity_0p6nnmc" />
    <bpmn:userTask id="Activity_116eb0m" name="Faça o pagamento">
      <bpmn:incoming>Flow_11lh8um</bpmn:incoming>
      <bpmn:outgoing>Flow_0f0a8qb</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:sequenceFlow id="Flow_0f0a8qb" sourceRef="Activity_116eb0m" targetRef="Activity_1prirvn" />
    <bpmn:intermediateCatchEvent id="Event_1jof7gr">
      <bpmn:incoming>Flow_1hbqx09</bpmn:incoming>
      <bpmn:outgoing>Flow_0176wdp</bpmn:outgoing>
      <bpmn:messageEventDefinition id="MessageEventDefinition_0suzcsp" />
    </bpmn:intermediateCatchEvent>
    <bpmn:sequenceFlow id="Flow_0176wdp" sourceRef="Event_1jof7gr" targetRef="Activity_1j5z80v" />
    <bpmn:intermediateCatchEvent id="Event_138egam">
      <bpmn:incoming>Flow_13u7s76</bpmn:incoming>
      <bpmn:outgoing>Flow_1v709ui</bpmn:outgoing>
      <bpmn:timerEventDefinition id="TimerEventDefinition_1fsvqz8" />
    </bpmn:intermediateCatchEvent>
    <bpmn:sequenceFlow id="Flow_13u7s76" sourceRef="Activity_05x4yc9" targetRef="Event_138egam" />
    <bpmn:exclusiveGateway id="Gateway_11arssd">
      <bpmn:incoming>Flow_1v709ui</bpmn:incoming>
      <bpmn:outgoing>Flow_1hbqx09</bpmn:outgoing>
      <bpmn:outgoing>Flow_19oozc1</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:sequenceFlow id="Flow_1hbqx09" name="Foi o maior lance" sourceRef="Gateway_11arssd" targetRef="Event_1jof7gr">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'yes'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:sequenceFlow id="Flow_19oozc1" name="Não foi o maior lançe" sourceRef="Gateway_11arssd" targetRef="Event_1f80boa">
      <bpmn:conditionExpression xsi:type="bpmn:tFormalExpression">#{'yes'}</bpmn:conditionExpression>
    </bpmn:sequenceFlow>
    <bpmn:sequenceFlow id="Flow_1v709ui" sourceRef="Event_138egam" targetRef="Gateway_11arssd" />
    <bpmn:endEvent id="Event_17l9eii">
      <bpmn:incoming>Flow_11vzu32</bpmn:incoming>
    </bpmn:endEvent>
    <bpmn:sequenceFlow id="Flow_11vzu32" sourceRef="Gateway_1i9z25w" targetRef="Event_17l9eii" />
    <bpmn:userTask id="Activity_05mg5v8" name="Faça o registro com nome, numero e         e-mail.">
      <bpmn:incoming>Flow_071rh36</bpmn:incoming>
      <bpmn:outgoing>Flow_1rzkf0d</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:sequenceFlow id="Flow_1rzkf0d" sourceRef="Activity_05mg5v8" targetRef="Activity_09vu229" />
    <bpmn:textAnnotation id="TextAnnotation_1krpdac">
      <bpmn:text>Os leilões tem um tempo, espere o tempo do leilão e ira receber uma notificação</bpmn:text>
    </bpmn:textAnnotation>
    <bpmn:association id="Association_08krhg7" sourceRef="Event_138egam" targetRef="TextAnnotation_1krpdac" />
    <bpmn:textAnnotation id="TextAnnotation_0nnw4s1">
      <bpmn:text>Pode finalizar o site se não achar o mineral desejado</bpmn:text>
    </bpmn:textAnnotation>
    <bpmn:association id="Association_06053n1" sourceRef="Event_17l9eii" targetRef="TextAnnotation_0nnw4s1" />
  </bpmn:process>
  <bpmndi:BPMNDiagram id="BPMNDiagram_1">
    <bpmndi:BPMNPlane id="BPMNPlane_1" bpmnElement="Collaboration_1kcd61k">
      <bpmndi:BPMNShape id="Participant_1nvxizg_di" bpmnElement="Participant_1nvxizg" isHorizontal="true">
        <dc:Bounds x="160" y="80" width="2808" height="650" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="TextAnnotation_0nnw4s1_di" bpmnElement="TextAnnotation_0nnw4s1">
        <dc:Bounds x="750" y="240" width="99.99156545209178" height="70.17543859649123" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="TextAnnotation_1krpdac_di" bpmnElement="TextAnnotation_1krpdac">
        <dc:Bounds x="1730" y="191" width="99.99156545209178" height="98.51551956815115" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_17oi0ci_di" bpmnElement="Activity_05mg5v8">
        <dc:Bounds x="1140" y="290" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_17l9eii_di" bpmnElement="Event_17l9eii">
        <dc:Bounds x="712" y="322" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_11arssd_di" bpmnElement="Gateway_11arssd" isMarkerVisible="true">
        <dc:Bounds x="1875" y="305" width="50" height="50" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_138egam_di" bpmnElement="Event_138egam">
        <dc:Bounds x="1722" y="312" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_1jof7gr_di" bpmnElement="Event_1jof7gr">
        <dc:Bounds x="1992" y="222" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_034lx8u_di" bpmnElement="Activity_116eb0m">
        <dc:Bounds x="2430" y="210" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0kyc38m_di" bpmnElement="Activity_1j5z80v">
        <dc:Bounds x="2080" y="200" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1r79pfj_di" bpmnElement="Activity_09vu229">
        <dc:Bounds x="1310" y="290" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0sub86u_di" bpmnElement="Activity_05x4yc9">
        <dc:Bounds x="1520" y="290" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_17jwkbg_di" bpmnElement="Activity_0p6nnmc">
        <dc:Bounds x="2250" y="210" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_024xm4e_di" bpmnElement="Activity_1prirvn">
        <dc:Bounds x="2560" y="210" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="BPMNShape_16u4c99" bpmnElement="Event_0ri09ng">
        <dc:Bounds x="2832" y="232" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_13r0l9f_di" bpmnElement="Activity_0d01tma">
        <dc:Bounds x="2700" y="210" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_07envfk_di" bpmnElement="Activity_07envfk">
        <dc:Bounds x="351" y="420" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_0f5jd9x_di" bpmnElement="Gateway_0f5jd9x" isMarkerVisible="true">
        <dc:Bounds x="886" y="445" width="50" height="50" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1m129fs_di" bpmnElement="Activity_0lcp96f">
        <dc:Bounds x="1360" y="530" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_0g3bexd_di" bpmnElement="Gateway_1i9z25w" isMarkerVisible="true">
        <dc:Bounds x="618" y="445" width="50" height="50" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1d0w2gu_di" bpmnElement="Activity_1d0w2gu">
        <dc:Bounds x="740" y="570" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_1xms693_di" bpmnElement="Event_1xms693">
        <dc:Bounds x="1782" y="552" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_1f80boa_di" bpmnElement="Event_1f80boa">
        <dc:Bounds x="1882" y="372" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1if8pd5_di" bpmnElement="Activity_03cah9k">
        <dc:Bounds x="1910" y="470" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_1upvtf7_di" bpmnElement="Event_13wkcdg">
        <dc:Bounds x="2002" y="592" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1g4il3g_di" bpmnElement="Activity_1wwvqeo">
        <dc:Bounds x="1160" y="530" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1l6iptv_di" bpmnElement="Activity_060no5w">
        <dc:Bounds x="1500" y="530" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_12tw2of_di" bpmnElement="Activity_0uj73k6">
        <dc:Bounds x="1640" y="530" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0uotljs_di" bpmnElement="Activity_1r1323j">
        <dc:Bounds x="491" y="420" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="_BPMNShape_StartEvent_2" bpmnElement="StartEvent_1">
        <dc:Bounds x="242" y="432" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNEdge id="Association_06053n1_di" bpmnElement="Association_06053n1">
        <di:waypoint x="741" y="326" />
        <di:waypoint x="755" y="310" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Association_08krhg7_di" bpmnElement="Association_08krhg7">
        <di:waypoint x="1746" y="313" />
        <di:waypoint x="1753" y="290" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_19umwci_di" bpmnElement="Flow_19umwci">
        <di:waypoint x="278" y="450" />
        <di:waypoint x="315" y="450" />
        <di:waypoint x="315" y="460" />
        <di:waypoint x="351" y="460" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_02ytm10_di" bpmnElement="Flow_02ytm10">
        <di:waypoint x="643" y="445" />
        <di:waypoint x="643" y="360" />
        <di:waypoint x="550" y="360" />
        <di:waypoint x="420" y="420" />
        <bpmndi:BPMNLabel color:color="#0d4372">
          <dc:Bounds x="576" y="316" width="58" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1jyjvh9_di" bpmnElement="Flow_1jyjvh9">
        <di:waypoint x="451" y="460" />
        <di:waypoint x="491" y="460" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_01lr78b_di" bpmnElement="Flow_01lr78b">
        <di:waypoint x="790" y="570" />
        <di:waypoint x="790" y="470" />
        <di:waypoint x="886" y="470" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_071rh36_di" bpmnElement="Flow_071rh36">
        <di:waypoint x="911" y="445" />
        <di:waypoint x="911" y="330" />
        <di:waypoint x="1140" y="330" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="961" y="333" width="77" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_13lxwun_di" bpmnElement="Flow_13lxwun">
        <di:waypoint x="911" y="495" />
        <di:waypoint x="911" y="570" />
        <di:waypoint x="1160" y="570" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="966" y="536" width="88" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_13jlfix_di" bpmnElement="Flow_13jlfix">
        <di:waypoint x="1260" y="570" />
        <di:waypoint x="1360" y="570" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1hazw25_di" bpmnElement="Flow_1hazw25">
        <di:waypoint x="1460" y="570" />
        <di:waypoint x="1500" y="570" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1q9pdjh_di" bpmnElement="Flow_1q9pdjh">
        <di:waypoint x="591" y="460" />
        <di:waypoint x="605" y="460" />
        <di:waypoint x="605" y="470" />
        <di:waypoint x="618" y="470" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1ysi6ld_di" bpmnElement="Flow_1ysi6ld">
        <di:waypoint x="643" y="495" />
        <di:waypoint x="643" y="533" />
        <di:waypoint x="621" y="533" />
        <di:waypoint x="621" y="610" />
        <di:waypoint x="740" y="610" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="623" y="593" width="89" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_11vzu32_di" bpmnElement="Flow_11vzu32">
        <di:waypoint x="663" y="465" />
        <di:waypoint x="730" y="450" />
        <di:waypoint x="730" y="358" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1rzkf0d_di" bpmnElement="Flow_1rzkf0d">
        <di:waypoint x="1240" y="330" />
        <di:waypoint x="1275" y="330" />
        <di:waypoint x="1275" y="350" />
        <di:waypoint x="1310" y="350" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0vqppic_di" bpmnElement="Flow_0vqppic">
        <di:waypoint x="1740" y="570" />
        <di:waypoint x="1782" y="570" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1v709ui_di" bpmnElement="Flow_1v709ui">
        <di:waypoint x="1758" y="330" />
        <di:waypoint x="1875" y="330" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_19oozc1_di" bpmnElement="Flow_19oozc1">
        <di:waypoint x="1900" y="355" />
        <di:waypoint x="1900" y="372" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="1922" y="376" width="76" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1hbqx09_di" bpmnElement="Flow_1hbqx09">
        <di:waypoint x="1900" y="305" />
        <di:waypoint x="1900" y="240" />
        <di:waypoint x="1992" y="240" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="1987" y="273" width="85" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_16uhnxs_di" bpmnElement="Flow_16uhnxs">
        <di:waypoint x="1900" y="408" />
        <di:waypoint x="1900" y="439" />
        <di:waypoint x="1960" y="439" />
        <di:waypoint x="1960" y="470" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_13u7s76_di" bpmnElement="Flow_13u7s76">
        <di:waypoint x="1620" y="330" />
        <di:waypoint x="1722" y="330" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0176wdp_di" bpmnElement="Flow_0176wdp">
        <di:waypoint x="2028" y="240" />
        <di:waypoint x="2054" y="240" />
        <di:waypoint x="2054" y="250" />
        <di:waypoint x="2080" y="250" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_11lh8um_di" bpmnElement="Flow_11lh8um">
        <di:waypoint x="2350" y="250" />
        <di:waypoint x="2430" y="250" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0f0a8qb_di" bpmnElement="Flow_0f0a8qb">
        <di:waypoint x="2530" y="250" />
        <di:waypoint x="2560" y="250" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0jq454g_di" bpmnElement="Flow_0jq454g">
        <di:waypoint x="2180" y="240" />
        <di:waypoint x="2250" y="240" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_02dqcmc_di" bpmnElement="Flow_02dqcmc">
        <di:waypoint x="1990" y="550" />
        <di:waypoint x="1990" y="571" />
        <di:waypoint x="2020" y="571" />
        <di:waypoint x="2020" y="592" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1vnc7gt_di" bpmnElement="Flow_1vnc7gt">
        <di:waypoint x="1410" y="330" />
        <di:waypoint x="1520" y="330" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_12s7na1_di" bpmnElement="Flow_12s7na1">
        <di:waypoint x="1600" y="570" />
        <di:waypoint x="1640" y="570" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0v251j5_di" bpmnElement="Flow_0v251j5">
        <di:waypoint x="2660" y="250" />
        <di:waypoint x="2700" y="250" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0oj1dyp_di" bpmnElement="Flow_0oj1dyp">
        <di:waypoint x="2800" y="250" />
        <di:waypoint x="2832" y="250" />
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
