### 3.3.3 Processo 3 – Avaliação e Feedback

```bpmn
<?xml version="1.0" encoding="UTF-8"?>
<bpmn:definitions xmlns:bpmn="http://www.omg.org/spec/BPMN/20100524/MODEL" xmlns:bpmndi="http://www.omg.org/spec/BPMN/20100524/DI" xmlns:dc="http://www.omg.org/spec/DD/20100524/DC" xmlns:di="http://www.omg.org/spec/DD/20100524/DI" xmlns:modeler="http://camunda.org/schema/modeler/1.0" xmlns:camunda="http://camunda.org/schema/1.0/bpmn" id="Definitions_1" targetNamespace="http://bpmn.io/schema/bpmn" exporter="Camunda Web Modeler" exporterVersion="cbae99f" modeler:executionPlatform="Camunda Cloud" modeler:executionPlatformVersion="8.2.0" camunda:diagramRelationId="3e80ba7a-32a9-47c2-bf76-3112efede4e1">
  <bpmn:collaboration id="Collaboration_13bk9sx">
    <bpmn:participant id="Participant_0r0fkny" name="Feedback e  Avaliação" processRef="Process_0ghmxe6" />
  </bpmn:collaboration>
  <bpmn:process id="Process_0ghmxe6" isExecutable="true">
    <bpmn:laneSet id="LaneSet_019mthn">
      <bpmn:lane id="Lane_0t5sejf" name="Usuário">
        <bpmn:flowNodeRef>Gateway_10ly13p</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Event_1sqldq1</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Gateway_06my4zd</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Event_1edru3p</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1mdr8b4</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1jz3lu7</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_0xsx0rm</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1yqcbxa</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1oxywt8</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1fbux4j</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1m9vx8d</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_0y7s27f</bpmn:flowNodeRef>
      </bpmn:lane>
      <bpmn:lane id="Lane_1d79h5l" name="Equipe de Denúncias">
        <bpmn:flowNodeRef>Gateway_0fpormg</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Event_02li1r4</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Gateway_0eg8fc8</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Gateway_02cr7kt</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Event_1uvsipy</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Event_0dr5frx</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1rcpdxe</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1l1bi9u</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_1hoivyp</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_0djwjpn</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_0wbcyrx</bpmn:flowNodeRef>
        <bpmn:flowNodeRef>Activity_17qhxah</bpmn:flowNodeRef>
      </bpmn:lane>
    </bpmn:laneSet>
    <bpmn:sequenceFlow id="Flow_00taaxl" name="Avaliar/Comentar" sourceRef="Gateway_10ly13p" targetRef="Activity_1jz3lu7" />
    <bpmn:sequenceFlow id="Flow_1p7qybu" name="Denunciar" sourceRef="Gateway_10ly13p" targetRef="Activity_1oxywt8" />
    <bpmn:sequenceFlow id="Flow_0df79mn" sourceRef="Activity_1jz3lu7" targetRef="Gateway_06my4zd" />
    <bpmn:sequenceFlow id="Flow_1dkndx2" name="Sim" sourceRef="Gateway_06my4zd" targetRef="Activity_0xsx0rm" />
    <bpmn:sequenceFlow id="Flow_1uudfr2" name="Não" sourceRef="Gateway_06my4zd" targetRef="Activity_1m9vx8d" />
    <bpmn:sequenceFlow id="Flow_18y0gsg" sourceRef="Activity_0xsx0rm" targetRef="Activity_1m9vx8d" />
    <bpmn:sequenceFlow id="Flow_0u2r97f" sourceRef="Activity_1m9vx8d" targetRef="Activity_1yqcbxa" />
    <bpmn:sequenceFlow id="Flow_1r1yhbn" sourceRef="Activity_1yqcbxa" targetRef="Event_1edru3p" />
    <bpmn:sequenceFlow id="Flow_0gewev4" sourceRef="Activity_1oxywt8" targetRef="Activity_1fbux4j" />
    <bpmn:sequenceFlow id="Flow_11lg5kj" sourceRef="Activity_1fbux4j" targetRef="Activity_0y7s27f" />
    <bpmn:sequenceFlow id="Flow_10ed4pn" sourceRef="Activity_0y7s27f" targetRef="Activity_1rcpdxe" />
    <bpmn:sequenceFlow id="Flow_1b6256r" name="Sim" sourceRef="Gateway_0fpormg" targetRef="Gateway_0eg8fc8" />
    <bpmn:sequenceFlow id="Flow_1lqfmbl" name="Não" sourceRef="Gateway_0fpormg" targetRef="Activity_0wbcyrx" />
    <bpmn:sequenceFlow id="Flow_1o0499k" name="Sim" sourceRef="Gateway_0eg8fc8" targetRef="Activity_1hoivyp" />
    <bpmn:sequenceFlow id="Flow_0qf62zg" sourceRef="Activity_1hoivyp" targetRef="Activity_1l1bi9u" />
    <bpmn:sequenceFlow id="Flow_0bi90op" name="Não" sourceRef="Gateway_0eg8fc8" targetRef="Activity_0djwjpn" />
    <bpmn:sequenceFlow id="Flow_1oss8bx" sourceRef="Activity_0wbcyrx" targetRef="Event_02li1r4" />
    <bpmn:sequenceFlow id="Flow_0fqyeim" sourceRef="Activity_1rcpdxe" targetRef="Gateway_0fpormg" />
    <bpmn:sequenceFlow id="Flow_04tbodj" name="Não Comentar/ Denunciar" sourceRef="Gateway_10ly13p" targetRef="Activity_1yqcbxa" />
    <bpmn:sequenceFlow id="Flow_1mkzzid" sourceRef="Activity_0djwjpn" targetRef="Gateway_02cr7kt" />
    <bpmn:sequenceFlow id="Flow_1qq5vxa" name="Não" sourceRef="Gateway_02cr7kt" targetRef="Activity_1hoivyp" />
    <bpmn:sequenceFlow id="Flow_0jvm9at" name="Sim" sourceRef="Gateway_02cr7kt" targetRef="Activity_17qhxah" />
    <bpmn:sequenceFlow id="Flow_1dqnj4t" sourceRef="Activity_17qhxah" targetRef="Event_1uvsipy" />
    <bpmn:sequenceFlow id="Flow_0zlq73o" sourceRef="Activity_1l1bi9u" targetRef="Event_0dr5frx" />
    <bpmn:sequenceFlow id="Flow_0mrh760" sourceRef="Activity_1mdr8b4" targetRef="Gateway_10ly13p" />
    <bpmn:exclusiveGateway id="Gateway_10ly13p" name="Escolher intenção">
      <bpmn:incoming>Flow_0mrh760</bpmn:incoming>
      <bpmn:outgoing>Flow_00taaxl</bpmn:outgoing>
      <bpmn:outgoing>Flow_1p7qybu</bpmn:outgoing>
      <bpmn:outgoing>Flow_04tbodj</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:startEvent id="Event_1sqldq1" name="Efetuação do Pagamento" />
    <bpmn:exclusiveGateway id="Gateway_0fpormg" name="a denúncia é consistente?">
      <bpmn:incoming>Flow_0fqyeim</bpmn:incoming>
      <bpmn:outgoing>Flow_1b6256r</bpmn:outgoing>
      <bpmn:outgoing>Flow_1lqfmbl</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:endEvent id="Event_02li1r4">
      <bpmn:incoming>Flow_1oss8bx</bpmn:incoming>
    </bpmn:endEvent>
    <bpmn:exclusiveGateway id="Gateway_06my4zd" name="usuário deseja realizar um comentário?">
      <bpmn:incoming>Flow_0df79mn</bpmn:incoming>
      <bpmn:outgoing>Flow_1dkndx2</bpmn:outgoing>
      <bpmn:outgoing>Flow_1uudfr2</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:endEvent id="Event_1edru3p">
      <bpmn:incoming>Flow_1r1yhbn</bpmn:incoming>
    </bpmn:endEvent>
    <bpmn:exclusiveGateway id="Gateway_0eg8fc8" name="é recorrente as denúncias contra esse vendedor?">
      <bpmn:incoming>Flow_1b6256r</bpmn:incoming>
      <bpmn:outgoing>Flow_1o0499k</bpmn:outgoing>
      <bpmn:outgoing>Flow_0bi90op</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:exclusiveGateway id="Gateway_02cr7kt" name="o problema foi explicado de forma satisfatória?">
      <bpmn:incoming>Flow_1mkzzid</bpmn:incoming>
      <bpmn:outgoing>Flow_1qq5vxa</bpmn:outgoing>
      <bpmn:outgoing>Flow_0jvm9at</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:endEvent id="Event_1uvsipy">
      <bpmn:incoming>Flow_1dqnj4t</bpmn:incoming>
    </bpmn:endEvent>
    <bpmn:endEvent id="Event_0dr5frx">
      <bpmn:incoming>Flow_0zlq73o</bpmn:incoming>
    </bpmn:endEvent>
    <bpmn:serviceTask id="Activity_1mdr8b4" name="Disponibiliza a página de Feedback">
      <bpmn:outgoing>Flow_0mrh760</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:userTask id="Activity_1jz3lu7" name="Escolhe uma nota de 1 a 5 estrelas">
      <bpmn:incoming>Flow_00taaxl</bpmn:incoming>
      <bpmn:outgoing>Flow_0df79mn</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:userTask id="Activity_0xsx0rm" name="Preenche um comentário junto da avaliação">
      <bpmn:incoming>Flow_1dkndx2</bpmn:incoming>
      <bpmn:outgoing>Flow_18y0gsg</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:serviceTask id="Activity_1yqcbxa" name="Mantém Feedback visível publicamente  para consulta.">
      <bpmn:incoming>Flow_0u2r97f</bpmn:incoming>
      <bpmn:incoming>Flow_04tbodj</bpmn:incoming>
      <bpmn:outgoing>Flow_1r1yhbn</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:userTask id="Activity_1oxywt8" name="Abre uma denúncia com uma descrição do problema">
      <bpmn:incoming>Flow_1p7qybu</bpmn:incoming>
      <bpmn:outgoing>Flow_0gewev4</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:userTask id="Activity_1fbux4j" name="anexa evidências do ocorrido, como fotos ou arquivos">
      <bpmn:incoming>Flow_0gewev4</bpmn:incoming>
      <bpmn:outgoing>Flow_11lg5kj</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:serviceTask id="Activity_1m9vx8d" name="Envia o feedback pro perfil do vendedor">
      <bpmn:incoming>Flow_1uudfr2</bpmn:incoming>
      <bpmn:incoming>Flow_18y0gsg</bpmn:incoming>
      <bpmn:outgoing>Flow_0u2r97f</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:receiveTask id="Activity_1rcpdxe" name="Recebe a denúncia e inicia o processo de análise">
      <bpmn:incoming>Flow_10ed4pn</bpmn:incoming>
      <bpmn:outgoing>Flow_0fqyeim</bpmn:outgoing>
    </bpmn:receiveTask>
    <bpmn:sendTask id="Activity_0y7s27f" name="envia a denuncia para a equipe de denuncias">
      <bpmn:incoming>Flow_11lg5kj</bpmn:incoming>
      <bpmn:outgoing>Flow_10ed4pn</bpmn:outgoing>
    </bpmn:sendTask>
    <bpmn:userTask id="Activity_1l1bi9u" name="Encaminha a denúncia e o histórico para as autoridades">
      <bpmn:incoming>Flow_0qf62zg</bpmn:incoming>
      <bpmn:outgoing>Flow_0zlq73o</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:userTask id="Activity_1hoivyp" name="Realiza o encerramento da conta do vendedor">
      <bpmn:incoming>Flow_1o0499k</bpmn:incoming>
      <bpmn:incoming>Flow_1qq5vxa</bpmn:incoming>
      <bpmn:outgoing>Flow_0qf62zg</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:userTask id="Activity_0djwjpn" name="Entra em contato com o vendedor para buscar informações">
      <bpmn:incoming>Flow_0bi90op</bpmn:incoming>
      <bpmn:outgoing>Flow_1mkzzid</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:userTask id="Activity_0wbcyrx" name="A denúncia é descartada">
      <bpmn:incoming>Flow_1lqfmbl</bpmn:incoming>
      <bpmn:outgoing>Flow_1oss8bx</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:userTask id="Activity_17qhxah" name="comunica para o comprador o ocorrido">
      <bpmn:incoming>Flow_0jvm9at</bpmn:incoming>
      <bpmn:outgoing>Flow_1dqnj4t</bpmn:outgoing>
    </bpmn:userTask>
  </bpmn:process>
  <bpmndi:BPMNDiagram id="BPMNDiagram_1">
    <bpmndi:BPMNPlane id="BPMNPlane_1" bpmnElement="Collaboration_13bk9sx">
      <bpmndi:BPMNShape id="Participant_0r0fkny_di" bpmnElement="Participant_0r0fkny" isHorizontal="true">
        <dc:Bounds x="160" y="50" width="1320" height="950" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Lane_1d79h5l_di" bpmnElement="Lane_1d79h5l" isHorizontal="true">
        <dc:Bounds x="190" y="630" width="1290" height="370" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Lane_0t5sejf_di" bpmnElement="Lane_0t5sejf" isHorizontal="true">
        <dc:Bounds x="190" y="50" width="1290" height="580" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_10ly13p_di" bpmnElement="Gateway_10ly13p" isMarkerVisible="true">
        <dc:Bounds x="455" y="305" width="50" height="50" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="515" y="273" width="88" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_1sqldq1_di" bpmnElement="Event_1sqldq1">
        <dc:Bounds x="232" y="287" width="36" height="36" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="218" y="330" width="65" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_0fpormg_di" bpmnElement="Gateway_0fpormg" isMarkerVisible="true">
        <dc:Bounds x="455" y="745" width="50" height="50" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="514.5" y="756" width="63" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_02li1r4_di" bpmnElement="Event_02li1r4">
        <dc:Bounds x="332" y="882" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_06my4zd_di" bpmnElement="Gateway_06my4zd" isMarkerVisible="true">
        <dc:Bounds x="765" y="125" width="50" height="50" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="754" y="75" width="72" height="40" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_1edru3p_di" bpmnElement="Event_1edru3p">
        <dc:Bounds x="1192" y="132" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_0eg8fc8_di" bpmnElement="Gateway_0eg8fc8" isMarkerVisible="true">
        <dc:Bounds x="665" y="675" width="50" height="50" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="698" y="710" width="84" height="40" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_02cr7kt_di" bpmnElement="Gateway_02cr7kt" isMarkerVisible="true">
        <dc:Bounds x="905" y="875" width="50" height="50" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="889" y="932" width="90" height="40" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_1uvsipy_di" bpmnElement="Event_1uvsipy">
        <dc:Bounds x="1282" y="882" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_0dr5frx_di" bpmnElement="Event_0dr5frx">
        <dc:Bounds x="1282" y="682" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0xc6ao2_di" bpmnElement="Activity_1mdr8b4">
        <dc:Bounds x="320" y="265" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_066stea_di" bpmnElement="Activity_1jz3lu7">
        <dc:Bounds x="620" y="110" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1myw6so_di" bpmnElement="Activity_0xsx0rm">
        <dc:Bounds x="740" y="265" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1ggsjhq_di" bpmnElement="Activity_1yqcbxa">
        <dc:Bounds x="1050" y="110" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_02wktz3_di" bpmnElement="Activity_1oxywt8">
        <dc:Bounds x="620" y="470" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1ucm776_di" bpmnElement="Activity_1fbux4j">
        <dc:Bounds x="840" y="470" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_07d1yb7_di" bpmnElement="Activity_1m9vx8d">
        <dc:Bounds x="880" y="110" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_196kgzr_di" bpmnElement="Activity_1rcpdxe">
        <dc:Bounds x="290" y="650" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1j6o1pt_di" bpmnElement="Activity_0y7s27f">
        <dc:Bounds x="1060" y="470" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_13eguc5_di" bpmnElement="Activity_1l1bi9u">
        <dc:Bounds x="1130" y="660" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0jm0d9j_di" bpmnElement="Activity_1hoivyp">
        <dc:Bounds x="880" y="660" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1hd5c5v_di" bpmnElement="Activity_0djwjpn">
        <dc:Bounds x="640" y="860" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0ngnalu_di" bpmnElement="Activity_0wbcyrx">
        <dc:Bounds x="430" y="860" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1vzp9yy_di" bpmnElement="Activity_17qhxah">
        <dc:Bounds x="1120" y="860" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNEdge id="Flow_00taaxl_di" bpmnElement="Flow_00taaxl">
        <di:waypoint x="480" y="305" />
        <di:waypoint x="480" y="150" />
        <di:waypoint x="620" y="150" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="503" y="153" width="86" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1p7qybu_di" bpmnElement="Flow_1p7qybu">
        <di:waypoint x="480" y="355" />
        <di:waypoint x="480" y="510" />
        <di:waypoint x="620" y="510" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="520" y="495" width="52" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0df79mn_di" bpmnElement="Flow_0df79mn">
        <di:waypoint x="720" y="150" />
        <di:waypoint x="765" y="150" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1dkndx2_di" bpmnElement="Flow_1dkndx2">
        <di:waypoint x="790" y="175" />
        <di:waypoint x="790" y="265" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="796" y="218" width="19" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1uudfr2_di" bpmnElement="Flow_1uudfr2">
        <di:waypoint x="815" y="150" />
        <di:waypoint x="880" y="150" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="838" y="132" width="21" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_18y0gsg_di" bpmnElement="Flow_18y0gsg">
        <di:waypoint x="840" y="305" />
        <di:waypoint x="930" y="305" />
        <di:waypoint x="930" y="190" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0u2r97f_di" bpmnElement="Flow_0u2r97f">
        <di:waypoint x="980" y="150" />
        <di:waypoint x="1050" y="150" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1r1yhbn_di" bpmnElement="Flow_1r1yhbn">
        <di:waypoint x="1150" y="150" />
        <di:waypoint x="1192" y="150" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0gewev4_di" bpmnElement="Flow_0gewev4">
        <di:waypoint x="720" y="510" />
        <di:waypoint x="840" y="510" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_11lg5kj_di" bpmnElement="Flow_11lg5kj">
        <di:waypoint x="940" y="510" />
        <di:waypoint x="1060" y="510" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_10ed4pn_di" bpmnElement="Flow_10ed4pn">
        <di:waypoint x="1110" y="550" />
        <di:waypoint x="1110" y="580" />
        <di:waypoint x="340" y="580" />
        <di:waypoint x="340" y="650" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1b6256r_di" bpmnElement="Flow_1b6256r">
        <di:waypoint x="480" y="745" />
        <di:waypoint x="480" y="700" />
        <di:waypoint x="665" y="700" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="486" y="720" width="19" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1lqfmbl_di" bpmnElement="Flow_1lqfmbl">
        <di:waypoint x="480" y="795" />
        <di:waypoint x="480" y="860" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="485" y="825" width="21" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1o0499k_di" bpmnElement="Flow_1o0499k">
        <di:waypoint x="715" y="700" />
        <di:waypoint x="880" y="700" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="789" y="682" width="19" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0qf62zg_di" bpmnElement="Flow_0qf62zg">
        <di:waypoint x="980" y="700" />
        <di:waypoint x="1130" y="700" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0bi90op_di" bpmnElement="Flow_0bi90op">
        <di:waypoint x="690" y="725" />
        <di:waypoint x="690" y="860" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="696" y="790" width="21" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1oss8bx_di" bpmnElement="Flow_1oss8bx">
        <di:waypoint x="430" y="900" />
        <di:waypoint x="368" y="900" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0fqyeim_di" bpmnElement="Flow_0fqyeim">
        <di:waypoint x="340" y="730" />
        <di:waypoint x="340" y="770" />
        <di:waypoint x="455" y="770" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_04tbodj_di" bpmnElement="Flow_04tbodj">
        <di:waypoint x="494" y="341" />
        <di:waypoint x="540" y="380" />
        <di:waypoint x="1100" y="380" />
        <di:waypoint x="1100" y="190" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="562" y="337" width="76" height="27" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1mkzzid_di" bpmnElement="Flow_1mkzzid">
        <di:waypoint x="740" y="900" />
        <di:waypoint x="905" y="900" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1qq5vxa_di" bpmnElement="Flow_1qq5vxa">
        <di:waypoint x="930" y="875" />
        <di:waypoint x="930" y="740" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="935" y="805" width="21" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0jvm9at_di" bpmnElement="Flow_0jvm9at">
        <di:waypoint x="955" y="900" />
        <di:waypoint x="1120" y="900" />
        <bpmndi:BPMNLabel>
          <dc:Bounds x="1028" y="882" width="19" height="14" />
        </bpmndi:BPMNLabel>
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1dqnj4t_di" bpmnElement="Flow_1dqnj4t">
        <di:waypoint x="1220" y="900" />
        <di:waypoint x="1282" y="900" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0zlq73o_di" bpmnElement="Flow_0zlq73o">
        <di:waypoint x="1230" y="700" />
        <di:waypoint x="1282" y="700" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0mrh760_di" bpmnElement="Flow_0mrh760">
        <di:waypoint x="420" y="305" />
        <di:waypoint x="438" y="305" />
        <di:waypoint x="438" y="330" />
        <di:waypoint x="455" y="330" />
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
| Pontuação       | Seleção Única    |tem que estar entre 1 e 5|não tem   |
| Comentário      | Área de Texto   |entre 1 e 100 caracteres|não tem     |

| **Comandos**         |  **Destino**                   | **Tipo**       |
| ---                  | ---                            | ---            |
| Enviar Avaliação     | fim da atividade 1             |default         |


**Atividade 2 : Denúncia**

| **Campo**             | **Tipo**                 | **Restrições**                 | **Valor default**                          |
| ---                   | ---                      | ---                            | ---                                        |
| Descrição do problema | Área de Texto            | entre 1 e 100 caracteres       | não tem                                    |
| Evidências            | Arquivo                  | 5 Arquivos                     | não tem                                    |

| **Comandos**         |  **Destino**                   | **Tipo**          |
| ---                  | ---                            | ---               |
| Enviardenuncia       |fim da atividade 2              |                   |
|                      |                                |                   |

**Atividade 3 : Tratamento de Denúncia**

| **Campo**            | **Tipo**         | **Restrições** | **Valor default** |
| ---                  | ---              | ---            | ---               |
|Descrição da denúncia | Área de Texto    | nenhuma        | nenhum            |
|Aviso de restrição    | Área de texto    | nenhuma        | nenhum            |
|Arquivos              | Arquivo          | 5 arquivos     | nenhum            |


| **Comandos**         |  **Destino**                   | **Tipo**             |
| ---                  | ---                            | ---                  |
|Restringirconta       |Fim da Atividade 3              |                      |
|DescreverDenuncia     |fim da Atividade 3              |                      |

