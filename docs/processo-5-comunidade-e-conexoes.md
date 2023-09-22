### 3.3.5 Processo 5 – NOME DO PROCESSO
```bpmn 
<?xml version="1.0" encoding="UTF-8"?>
<bpmn:definitions xmlns:bpmn="http://www.omg.org/spec/BPMN/20100524/MODEL" xmlns:bpmndi="http://www.omg.org/spec/BPMN/20100524/DI" xmlns:dc="http://www.omg.org/spec/DD/20100524/DC" xmlns:di="http://www.omg.org/spec/DD/20100524/DI" xmlns:modeler="http://camunda.org/schema/modeler/1.0" xmlns:camunda="http://camunda.org/schema/1.0/bpmn" id="Definitions_1" targetNamespace="http://bpmn.io/schema/bpmn" exporter="Camunda Web Modeler" exporterVersion="cbae99f" modeler:executionPlatform="Camunda Cloud" modeler:executionPlatformVersion="8.2.0" camunda:diagramRelationId="3e80ba7a-32a9-47c2-bf76-3112efede4e1">
  <bpmn:collaboration id="Collaboration_13bk9sx">
    <bpmn:participant id="Participant_0r0fkny" name="Comunidade e conexão" processRef="Process_0ghmxe6" />
  </bpmn:collaboration>
  <bpmn:process id="Process_0ghmxe6" isExecutable="true">
    <bpmn:laneSet id="LaneSet_019mthn">
      <bpmn:lane id="Lane_0t5sejf" name="Usuário">
        <bpmn:flowNodeRef>Event_1ppckt5</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1mdr8b4</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Event_1sqldq1</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Gateway_10ly13p</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Event_1edru3p</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1m9vx8d</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1yd6lwo</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1yqcbxa</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1oxywt8</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Gateway_1okwd7l</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Event_1709qi2</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Gateway_0jql6nd</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_0y7s27f</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_057i59c</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1wb3cz6</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1igcews</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1cc7kkz</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_0b1fh07</bpmn:flowNodeRef>
      </bpmn:lane>
      <bpmn:lane id="Lane_1d79h5l" name="Equipe de Fórum">
        <bpmn:flowNodeRef>Activity_1rcpdxe</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Gateway_1pqr21k</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Event_19n4hgm</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1losv6j</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_0obleab</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1glause</bpmn:flowNodeRef>
      </bpmn:lane>
    </bpmn:laneSet>
    <bpmn:sequenceFlow id="Flow_00taaxl" name="Abrir discussão" sourceRef="Gateway_10ly13p" targetRef="Activity_1yd6lwo" />
    <bpmn:sequenceFlow id="Flow_1p7qybu" name="Acessar discussão" sourceRef="Gateway_10ly13p" targetRef="Activity_1oxywt8" />
    <bpmn:sequenceFlow id="Flow_0u2r97f" sourceRef="Activity_1m9vx8d" targetRef="Activity_1yqcbxa" />
    <bpmn:sequenceFlow id="Flow_0mrh760" sourceRef="Activity_1mdr8b4" targetRef="Gateway_10ly13p" />
    <bpmn:receiveTask id="Activity_1rcpdxe" name="Receba notificação de discussão iniciada">
      <bpmn:incoming>Flow_075g3ge</bpmn:incoming>
      <bpmn:outgoing>Flow_00tewg3</bpmn:outgoing>
    </bpmn:receiveTask>
    <bpmn:sequenceFlow id="Flow_0yi8qwq" sourceRef="Event_1sqldq1" targetRef="Activity_1mdr8b4" />
    <bpmn:sequenceFlow id="Flow_1oz9k5v" sourceRef="Activity_1yd6lwo" targetRef="Activity_1m9vx8d" />
    <bpmn:sequenceFlow id="Flow_1qhrvio" sourceRef="Gateway_0jql6nd" targetRef="Activity_0y7s27f" />
    <bpmn:sequenceFlow id="Flow_1finxte" sourceRef="Activity_0y7s27f" targetRef="Activity_057i59c" />
    <bpmn:endEvent id="Event_1ppckt5">
      <bpmn:incoming>Flow_19zl4rv</bpmn:incoming>
    </bpmn:endEvent>
    <bpmn:sequenceFlow id="Flow_19zl4rv" sourceRef="Activity_057i59c" targetRef="Event_1ppckt5" />
    <bpmn:sequenceFlow id="Flow_075g3ge" sourceRef="Activity_1yqcbxa" targetRef="Activity_1rcpdxe" />
    <bpmn:sequenceFlow id="Flow_00tewg3" sourceRef="Activity_1rcpdxe" targetRef="Activity_1losv6j" />
    <bpmn:sequenceFlow id="Flow_0vcwvzr" sourceRef="Activity_1losv6j" targetRef="Activity_1glause" />
    <bpmn:sequenceFlow id="Flow_0js8fry" sourceRef="Activity_1glause" targetRef="Activity_0b1fh07" />
    <bpmn:sequenceFlow id="Flow_1uzqw2n" sourceRef="Activity_0b1fh07" targetRef="Gateway_1pqr21k" />
    <bpmn:exclusiveGateway id="Gateway_1pqr21k" name="Cliente Satisfeito com a Resposta?">
      <bpmn:incoming>Flow_1uzqw2n</bpmn:incoming>
      <bpmn:outgoing>Flow_0b2545m</bpmn:outgoing>
      <bpmn:outgoing>Flow_1vugvsn</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:sequenceFlow id="Flow_0b2545m" name="Não" sourceRef="Gateway_1pqr21k" targetRef="Activity_1losv6j" />
    <bpmn:sequenceFlow id="Flow_1vugvsn" name="Sim" sourceRef="Gateway_1pqr21k" targetRef="Activity_0obleab" />
    <bpmn:endEvent id="Event_19n4hgm">
      <bpmn:incoming>Flow_1xjfjd4</bpmn:incoming>
    </bpmn:endEvent>
    <bpmn:sequenceFlow id="Flow_1xjfjd4" sourceRef="Activity_0obleab" targetRef="Event_19n4hgm" />
    <bpmn:serviceTask id="Activity_1mdr8b4" name="Disponibiliza acesso/criação de postagens">
      <bpmn:incoming>Flow_0yi8qwq</bpmn:incoming>
      <bpmn:outgoing>Flow_0mrh760</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:startEvent id="Event_1sqldq1" name="Acesso a página de Fórum">
      <bpmn:outgoing>Flow_0yi8qwq</bpmn:outgoing>
    </bpmn:startEvent>
    <bpmn:exclusiveGateway id="Gateway_10ly13p" name="Escolher opção">
      <bpmn:incoming>Flow_0mrh760</bpmn:incoming>
      <bpmn:outgoing>Flow_00taaxl</bpmn:outgoing>
      <bpmn:outgoing>Flow_1p7qybu</bpmn:outgoing>
      <bpmn:outgoing>Flow_0dyp58b</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:endEvent id="Event_1edru3p">
      <bpmn:incoming>Flow_0dyp58b</bpmn:incoming>
    </bpmn:endEvent>
    <bpmn:sequenceFlow id="Flow_0dyp58b" sourceRef="Gateway_10ly13p" targetRef="Event_1edru3p" />
    <bpmn:serviceTask id="Activity_1m9vx8d" name="Sistema posta para visualização pública">
      <bpmn:incoming>Flow_1oz9k5v</bpmn:incoming>
      <bpmn:outgoing>Flow_0u2r97f</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:userTask id="Activity_1yd6lwo" name="Descreve o Foco da Discussão/ Problema em questão">
      <bpmn:incoming>Flow_00taaxl</bpmn:incoming>
      <bpmn:outgoing>Flow_1oz9k5v</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:sendTask id="Activity_1yqcbxa" name="Notificar equipe de resposta">
      <bpmn:incoming>Flow_0u2r97f</bpmn:incoming>
      <bpmn:outgoing>Flow_075g3ge</bpmn:outgoing>
    </bpmn:sendTask>
    <bpmn:userTask id="Activity_1losv6j" name="Forneçe Resposta / Solução Técnica">
      <bpmn:incoming>Flow_00tewg3</bpmn:incoming>
      <bpmn:incoming>Flow_0b2545m</bpmn:incoming>
      <bpmn:outgoing>Flow_0vcwvzr</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:serviceTask id="Activity_0obleab" name="Encerra discussão no fórum">
      <bpmn:incoming>Flow_1vugvsn</bpmn:incoming>
      <bpmn:outgoing>Flow_1xjfjd4</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:serviceTask id="Activity_1glause" name="Notifica o usuário da resposta">
      <bpmn:incoming>Flow_0vcwvzr</bpmn:incoming>
      <bpmn:outgoing>Flow_0js8fry</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:sequenceFlow id="Flow_1i74z0y" name="Não " sourceRef="Gateway_0jql6nd" targetRef="Activity_1igcews" />
    <bpmn:serviceTask id="Activity_1oxywt8" name="Disponibiliza fóruns em aberto/fechado">
      <bpmn:incoming>Flow_1p7qybu</bpmn:incoming>
      <bpmn:outgoing>Flow_0f6xpcn</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:sequenceFlow id="Flow_0f6xpcn" sourceRef="Activity_1oxywt8" targetRef="Activity_1cc7kkz" />
    <bpmn:sequenceFlow id="Flow_1cy9bet" sourceRef="Activity_1cc7kkz" targetRef="Gateway_1okwd7l" />
    <bpmn:exclusiveGateway id="Gateway_1okwd7l" name="Discussão esta aberta?">
      <bpmn:incoming>Flow_1cy9bet</bpmn:incoming>
      <bpmn:outgoing>Flow_0eutq3m</bpmn:outgoing>
      <bpmn:outgoing>Flow_0q22yyx</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:sequenceFlow id="Flow_0eutq3m" sourceRef="Gateway_1okwd7l" targetRef="Activity_1wb3cz6" />
    <bpmn:sequenceFlow id="Flow_0q22yyx" sourceRef="Gateway_1okwd7l" targetRef="Activity_1igcews" />
    <bpmn:sequenceFlow id="Flow_0t99p5p" sourceRef="Activity_1igcews" targetRef="Event_1709qi2" />
    <bpmn:endEvent id="Event_1709qi2">
      <bpmn:incoming>Flow_0t99p5p</bpmn:incoming>
    </bpmn:endEvent>
    <bpmn:sequenceFlow id="Flow_11g1701" sourceRef="Activity_1wb3cz6" targetRef="Gateway_0jql6nd" />
    <bpmn:exclusiveGateway id="Gateway_0jql6nd" name="Deseja contribuir com a discussão?">
      <bpmn:incoming>Flow_11g1701</bpmn:incoming>
      <bpmn:outgoing>Flow_1i74z0y</bpmn:outgoing>
      <bpmn:outgoing>Flow_1qhrvio</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:userTask id="Activity_0y7s27f" name="usuario edita e envia contribuicao">
      <bpmn:incoming>Flow_1qhrvio</bpmn:incoming>
      <bpmn:outgoing>Flow_1finxte</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:serviceTask id="Activity_057i59c" name="Sistema disponibiliza publicamente a resposta">
      <bpmn:incoming>Flow_1finxte</bpmn:incoming>
      <bpmn:outgoing>Flow_19zl4rv</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:serviceTask id="Activity_1wb3cz6" name="oferece opcao de contribuir">
      <bpmn:incoming>Flow_0eutq3m</bpmn:incoming>
      <bpmn:outgoing>Flow_11g1701</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:userTask id="Activity_1igcews" name="cliente decide quando sair">
      <bpmn:incoming>Flow_0q22yyx</bpmn:incoming>
      <bpmn:incoming>Flow_1i74z0y</bpmn:incoming>
      <bpmn:outgoing>Flow_0t99p5p</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:userTask id="Activity_1cc7kkz" name="Usuário escolhe uma discussão">
      <bpmn:incoming>Flow_0f6xpcn</bpmn:incoming>
      <bpmn:outgoing>Flow_1cy9bet</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:userTask id="Activity_0b1fh07" name="Feedback do cliente com relacao a resposta">
      <bpmn:incoming>Flow_0js8fry</bpmn:incoming>
      <bpmn:outgoing>Flow_1uzqw2n</bpmn:outgoing>
    </bpmn:userTask>
  </bpmn:process>
  <bpmndi:BPMNDiagram id="BPMNDiagram_1">
    <bpmndi:BPMNPlane id="BPMNPlane_1" bpmnElement="Collaboration_13bk9sx">
      <bpmndi:BPMNShape id="Participant_0r0fkny_di" bpmnElement="Participant_0r0fkny" isHorizontal="true">
        <dc:Bounds x="160" y="50" width="1598" height="950" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Lane_1d79h5l_di" bpmnElement="Lane_1d79h5l" isHorizontal="true">
        <dc:Bounds x="190" y="630" width="1568" height="370" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Lane_0t5sejf_di" bpmnElement="Lane_0t5sejf" isHorizontal="true">
        <dc:Bounds x="190" y="50" width="1568" height="580" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_196kgzr_di" bpmnElement="Activity_1rcpdxe">
        <dc:Bounds x="290" y="650" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_1ppckt5_di" bpmnElement="Event_1ppckt5">
        <dc:Bounds x="1622" y="492" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_1pqr21k_di" bpmnElement="Gateway_1pqr21k" isMarkerVisible="true">
        <dc:Bounds x="1015" y="705" width="50" height="50" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="930" y="710" width="79" height="40" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_19n4hgm_di" bpmnElement="Event_19n4hgm">
        <dc:Bounds x="1422" y="712" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0xc6ao2_di" bpmnElement="Activity_1mdr8b4">
        <dc:Bounds x="320" y="300" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_1sqldq1_di" bpmnElement="Event_1sqldq1">
        <dc:Bounds x="252" y="322" width="36" height="36" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="230" y="365" width="82" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_10ly13p_di" bpmnElement="Gateway_10ly13p" isMarkerVisible="true">
        <dc:Bounds x="455" y="315" width="50" height="50" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="382" y="283" width="76" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_1edru3p_di" bpmnElement="Event_1edru3p">
        <dc:Bounds x="672" y="322" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_07d1yb7_di" bpmnElement="Activity_1m9vx8d">
        <dc:Bounds x="720" y="190" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1agghbu_di" bpmnElement="Activity_1yd6lwo">
        <dc:Bounds x="560" y="190" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0wjqemd_di" bpmnElement="Activity_1yqcbxa">
        <dc:Bounds x="870" y="190" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0rdh8qq_di" bpmnElement="Activity_1losv6j">
        <dc:Bounds x="490" y="690" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1jv72ao_di" bpmnElement="Activity_0obleab">
        <dc:Bounds x="1190" y="690" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0v9cd34_di" bpmnElement="Activity_1glause">
        <dc:Bounds x="700" y="690" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1bmm26y_di" bpmnElement="Activity_1oxywt8">
        <dc:Bounds x="620" y="470" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_1okwd7l_di" bpmnElement="Gateway_1okwd7l" isMarkerVisible="true">
        <dc:Bounds x="1005" y="485" width="50" height="50" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="992" y="545" width="75" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_1709qi2_di" bpmnElement="Event_1709qi2">
        <dc:Bounds x="1012" y="252" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_0jql6nd_di" bpmnElement="Gateway_0jql6nd" isMarkerVisible="true">
        <dc:Bounds x="1145" y="345" width="50" height="50" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="1185" y="316" width="89" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_017wpj1_di" bpmnElement="Activity_0y7s27f">
        <dc:Bounds x="1410" y="360" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0fv9pd4_di" bpmnElement="Activity_057i59c">
        <dc:Bounds x="1410" y="470" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0xtry57_di" bpmnElement="Activity_1wb3cz6">
        <dc:Bounds x="1120" y="470" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1snrx66_di" bpmnElement="Activity_1igcews">
        <dc:Bounds x="980" y="330" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_06glesi_di" bpmnElement="Activity_1cc7kkz">
        <dc:Bounds x="840" y="470" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_04ongo0_di" bpmnElement="Activity_0b1fh07">
        <dc:Bounds x="490" y="520" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNEdge id="Flow_00taaxl_di" bpmnElement="Flow_00taaxl">
        <di:waypoint x="480" y="315" />
        <di:waypoint x="480" y="230" />
        <di:waypoint x="560" y="230" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="444" y="157" width="76" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1p7qybu_di" bpmnElement="Flow_1p7qybu">
        <di:waypoint x="480" y="365" />
        <di:waypoint x="480" y="420" />
        <di:waypoint x="670" y="420" />
        <di:waypoint x="670" y="470" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="547" y="428" width="49" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0u2r97f_di" bpmnElement="Flow_0u2r97f">
        <di:waypoint x="820" y="230" />
        <di:waypoint x="870" y="230" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0mrh760_di" bpmnElement="Flow_0mrh760">
        <di:waypoint x="420" y="340" />
        <di:waypoint x="455" y="340" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0yi8qwq_di" bpmnElement="Flow_0yi8qwq">
        <di:waypoint x="288" y="340" />
        <di:waypoint x="320" y="340" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1oz9k5v_di" bpmnElement="Flow_1oz9k5v">
        <di:waypoint x="660" y="230" />
        <di:waypoint x="720" y="230" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1qhrvio_di" bpmnElement="Flow_1qhrvio">
        <di:waypoint x="1195" y="370" />
        <di:waypoint x="1303" y="370" />
        <di:waypoint x="1303" y="400" />
        <di:waypoint x="1410" y="400" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1finxte_di" bpmnElement="Flow_1finxte">
        <di:waypoint x="1460" y="440" />
        <di:waypoint x="1460" y="470" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_19zl4rv_di" bpmnElement="Flow_19zl4rv">
        <di:waypoint x="1510" y="510" />
        <di:waypoint x="1622" y="510" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_075g3ge_di" bpmnElement="Flow_075g3ge">
        <di:waypoint x="920" y="190" />
        <di:waypoint x="920" y="80" />
        <di:waypoint x="220" y="80" />
        <di:waypoint x="220" y="700" />
        <di:waypoint x="290" y="700" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_00tewg3_di" bpmnElement="Flow_00tewg3">
        <di:waypoint x="390" y="690" />
        <di:waypoint x="410" y="690" />
        <di:waypoint x="410" y="730" />
        <di:waypoint x="490" y="730" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0vcwvzr_di" bpmnElement="Flow_0vcwvzr">
        <di:waypoint x="590" y="730" />
        <di:waypoint x="700" y="730" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0js8fry_di" bpmnElement="Flow_0js8fry">
        <di:waypoint x="797" y="766" />
        <di:waypoint x="860" y="815" />
        <di:waypoint x="440" y="815" />
        <di:waypoint x="460" y="560" />
        <di:waypoint x="490" y="560" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1uzqw2n_di" bpmnElement="Flow_1uzqw2n">
        <di:waypoint x="540" y="600" />
        <di:waypoint x="540" y="663" />
        <di:waypoint x="1040" y="663" />
        <di:waypoint x="1040" y="705" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0b2545m_di" bpmnElement="Flow_0b2545m">
        <di:waypoint x="1040" y="755" />
        <di:waypoint x="1040" y="870" />
        <di:waypoint x="520" y="870" />
        <di:waypoint x="520" y="770" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="754" y="852" width="21" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1vugvsn_di" bpmnElement="Flow_1vugvsn">
        <di:waypoint x="1065" y="730" />
        <di:waypoint x="1190" y="730" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="1118" y="712" width="19" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1xjfjd4_di" bpmnElement="Flow_1xjfjd4">
        <di:waypoint x="1290" y="730" />
        <di:waypoint x="1422" y="730" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0dyp58b_di" bpmnElement="Flow_0dyp58b">
        <di:waypoint x="505" y="340" />
        <di:waypoint x="672" y="340" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1i74z0y_di" bpmnElement="Flow_1i74z0y">
        <di:waypoint x="1145" y="370" />
        <di:waypoint x="1080" y="370" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="1102" y="352" width="21" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0f6xpcn_di" bpmnElement="Flow_0f6xpcn">
        <di:waypoint x="720" y="510" />
        <di:waypoint x="840" y="510" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1cy9bet_di" bpmnElement="Flow_1cy9bet">
        <di:waypoint x="940" y="510" />
        <di:waypoint x="1005" y="510" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0eutq3m_di" bpmnElement="Flow_0eutq3m">
        <di:waypoint x="1055" y="510" />
        <di:waypoint x="1120" y="510" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0q22yyx_di" bpmnElement="Flow_0q22yyx">
        <di:waypoint x="1030" y="485" />
        <di:waypoint x="1030" y="410" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0t99p5p_di" bpmnElement="Flow_0t99p5p">
        <di:waypoint x="1030" y="330" />
        <di:waypoint x="1030" y="288" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_11g1701_di" bpmnElement="Flow_11g1701">
        <di:waypoint x="1170" y="470" />
        <di:waypoint x="1170" y="395" />
      </bpmndi:BPMNEdge>
    </bpmndi:BPMNPlane>
  </bpmndi:BPMNDiagram>
</bpmn:definitions>

```


#### Detalhamento das atividades

Descrever aqui cada uma das propriedades das atividades do processo 3. 
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

**Atividade 1 : Avaliação/Comentário**

| **Campo**       | **Tipo**         | **Restrições** | **Valor default** |
| ---             | ---              | ---            | ---               |
| Engajamento       | Seleção Única    |tem que estar entre 1 e 5|não tem   |
| Feedback da Atividade	      | Área de Texto   |entre 1 e 100 caracteres|não tem     |

| **Comandos**         |  **Destino**                   | **Tipo**       |
| ---                  | ---                            | ---            |
| Enviar Feedback     | fim da atividade 1             |default         |


**Atividade 2 : Denúncia**

| **Campo**             | **Tipo**                 | **Restrições**                 | **Valor default**                          |
| ---                   | ---                      | ---                            | ---                                        |
| Membro Conectado	 | Área de Texto            | entre 1 e 100 caracteres       | não tem                                    |
| Tipo de Conexão	            | Arquivo                  | 5 Arquivos                     | não tem                                    |

| **Comandos**         |  **Destino**                   | **Tipo**          |
| ---                  | ---                            | ---               |
| Registrar Conexão	       |fim da atividade 2              |                   |
|                      |                                |                   |

**Atividade 3 : Tratamento de Denúncia**

| **Campo**            | **Tipo**         | **Restrições** | **Valor default** |
| ---                  | ---              | ---            | ---               |
|Nome da Conexão	 | Área de Texto    | nenhuma        | nenhum            |
|Impressão da Conexão	    | Área de texto    | nenhuma        | nenhum            |
|Sugestões              | Área de Texto	          | nenhuma     | nenhum            |


| **Comandos**         |  **Destino**                   | **Tipo**             |
| ---                  | ---                            | ---                  |
|Enviar Feedback	       |Fim da Atividade 3              |                      |
|Arquivar Feedback	     |fim da Atividade 3              |                      |
