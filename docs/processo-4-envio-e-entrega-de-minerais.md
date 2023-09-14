### 3.3.4 Processo 4 – ENVIO E ENTREGA DE MINERAIS

Apresente aqui o nome e as oportunidades de melhorias para o processo 4. 
Em seguida, apresente o modelo do processo 4, descrito no padrão BPMN.

```bpmn
<?xml version="1.0" encoding="UTF-8"?>
<bpmn:definitions xmlns:bpmn="http://www.omg.org/spec/BPMN/20100524/MODEL" xmlns:bpmndi="http://www.omg.org/spec/BPMN/20100524/DI" xmlns:dc="http://www.omg.org/spec/DD/20100524/DC" xmlns:di="http://www.omg.org/spec/DD/20100524/DI" xmlns:modeler="http://camunda.org/schema/modeler/1.0" id="Definitions_1jou7zz" targetNamespace="http://bpmn.io/schema/bpmn" exporter="Camunda Modeler" exporterVersion="5.15.0" modeler:executionPlatform="Camunda Cloud" modeler:executionPlatformVersion="8.2.0">
  <bpmn:collaboration id="Collaboration_1ld5vss">
    <bpmn:participant id="Participant_01uqcw9" processRef="Process_0xcsmws" />
  </bpmn:collaboration>
  <bpmn:process id="Process_0xcsmws" isExecutable="true">
    <bpmn:userTask id="Activity_1ll7lo7" name="COMPRA NO SITE">
      <bpmn:outgoing>Flow_122atbm</bpmn:outgoing>
    </bpmn:userTask>
    <bpmn:serviceTask id="Activity_0t16hfy" name="SOLICITAÇÃO PARA API">
      <bpmn:incoming>Flow_122atbm</bpmn:incoming>
      <bpmn:outgoing>Flow_021od0a</bpmn:outgoing>
    </bpmn:serviceTask>
    <bpmn:sequenceFlow id="Flow_122atbm" sourceRef="Activity_1ll7lo7" targetRef="Activity_0t16hfy" />
    <bpmn:sequenceFlow id="Flow_021od0a" sourceRef="Activity_0t16hfy" targetRef="Activity_0wfogdu" />
    <bpmn:sequenceFlow id="Flow_17t4m6y" sourceRef="Gateway_0yd3z1q" targetRef="Activity_1qvtakv" />
    <bpmn:sequenceFlow id="Flow_0olcout" sourceRef="Gateway_0yd3z1q" targetRef="Activity_1c2pabl" />
    <bpmn:task id="Activity_0wfogdu" name="VERIFIÇÃO DO ENDEREÇO DO COMPRADOR">
      <bpmn:incoming>Flow_021od0a</bpmn:incoming>
      <bpmn:outgoing>Flow_0x6913t</bpmn:outgoing>
    </bpmn:task>
    <bpmn:sequenceFlow id="Flow_0x6913t" sourceRef="Activity_0wfogdu" targetRef="Activity_0noziv3" />
    <bpmn:task id="Activity_1qvtakv" name="ENVIO DE CODIGO DE RASTREIO PARA O CLIENTE">
      <bpmn:incoming>Flow_17t4m6y</bpmn:incoming>
    </bpmn:task>
    <bpmn:task id="Activity_1c2pabl" name="ENVIO DA ETIQUETA PARA O FORNECEDOR">
      <bpmn:incoming>Flow_0olcout</bpmn:incoming>
    </bpmn:task>
    <bpmn:parallelGateway id="Gateway_0yd3z1q">
      <bpmn:incoming>Flow_17bgggx</bpmn:incoming>
      <bpmn:outgoing>Flow_17t4m6y</bpmn:outgoing>
      <bpmn:outgoing>Flow_0olcout</bpmn:outgoing>
    </bpmn:parallelGateway>
    <bpmn:task id="Activity_0noziv3" name="ESCOLHA DA OPÇAO DE FRETE&#10;(EMPRESA DE TRANSPORTE)">
      <bpmn:incoming>Flow_0x6913t</bpmn:incoming>
      <bpmn:outgoing>Flow_17bgggx</bpmn:outgoing>
    </bpmn:task>
    <bpmn:sequenceFlow id="Flow_17bgggx" sourceRef="Activity_0noziv3" targetRef="Gateway_0yd3z1q" />
  </bpmn:process>
  <bpmndi:BPMNDiagram id="BPMNDiagram_1">
    <bpmndi:BPMNPlane id="BPMNPlane_1" bpmnElement="Collaboration_1ld5vss">
      <bpmndi:BPMNShape id="Participant_01uqcw9_di" bpmnElement="Participant_01uqcw9" isHorizontal="true">
        <dc:Bounds x="135" y="50" width="905" height="360" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1ll7lo7_di" bpmnElement="Activity_1ll7lo7">
        <dc:Bounds x="190" y="170" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0t16hfy_di" bpmnElement="Activity_0t16hfy">
        <dc:Bounds x="340" y="170" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0wfogdu_di" bpmnElement="Activity_0wfogdu">
        <dc:Bounds x="500" y="170" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1qvtakv_di" bpmnElement="Activity_1qvtakv">
        <dc:Bounds x="880" y="170" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_1c2pabl_di" bpmnElement="Activity_1c2pabl">
        <dc:Bounds x="880" y="280" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_0yd3z1q_di" bpmnElement="Gateway_0yd3z1q">
        <dc:Bounds x="775" y="185" width="50" height="50" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0noziv3_di" bpmnElement="Activity_0noziv3">
        <dc:Bounds x="640" y="170" width="100" height="80" />
        <bpmndi:BPMNLabel />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNEdge id="Flow_122atbm_di" bpmnElement="Flow_122atbm">
        <di:waypoint x="290" y="210" />
        <di:waypoint x="340" y="210" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_021od0a_di" bpmnElement="Flow_021od0a">
        <di:waypoint x="440" y="210" />
        <di:waypoint x="500" y="210" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_17t4m6y_di" bpmnElement="Flow_17t4m6y">
        <di:waypoint x="825" y="210" />
        <di:waypoint x="880" y="210" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0olcout_di" bpmnElement="Flow_0olcout">
        <di:waypoint x="800" y="235" />
        <di:waypoint x="800" y="320" />
        <di:waypoint x="880" y="320" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0x6913t_di" bpmnElement="Flow_0x6913t">
        <di:waypoint x="600" y="210" />
        <di:waypoint x="640" y="210" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_17bgggx_di" bpmnElement="Flow_17bgggx">
        <di:waypoint x="740" y="210" />
        <di:waypoint x="775" y="210" />
      </bpmndi:BPMNEdge>
    </bpmndi:BPMNPlane>
  </bpmndi:BPMNDiagram>
</bpmn:definitions>
```



#### Detalhamento das atividades

Descrever aqui cada uma das propriedades das atividades do processo 4. 
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
| Identificação do Mineral	 |Caixa de Texto  |  Não pode estar vazio              |                   |
| Quantidade  |  Número                |    Valor >0            |     1              |
| data de envio          | data   | nao pode ser data da fatura |        data atual        |
| hora do envio           | hora   | - |           | hora atuaL

|Imagem do Mineral |	Imagem |	Formatos: .jpg, .png	-
|Origem |	Seleção única |	Opções: Mina A, Mina B, Mina C	-
|Destino |	Seleção única |	Opções: Porto A, Porto B, Porto C	-
|Documentos Associados |	Arquivo	Formatos: .pdf, .docx	-
|Link de Rastreamento |	Link |	Deve começar com "http://" ou "https://"	-







| **Comandos**         |  **Destino**                   | **Tipo** |
| Confirmar Envio | Atividade: Confirmação de Envio  | (default/cancel/  ) |
| Cancelar      |    Início do Processo                            |       cancel            |




