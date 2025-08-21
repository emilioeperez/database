# Lab 7: Walk through the usage of the Template Gallery and Agent Builder features

## Introduction

In this lab session, you will learn how to leverage the Template Gallery and the Agent Builder within Oracle Private AI Agent Studio to accelerate your workflow with minimal setup.

**Estimated time:** 20 minutes.

### Objectives

By the end of this lab, you will be able to:

- Explore the Template Gallery to identify and utilize pre-built workflow templates for a wide range of automation scenarios.
- Learn how to import and configure templates to quickly deploy AI-powered agents.
- Familiarize yourself with the Agent Builder to visually design, assemble, and automate new workflows using diverse components.
- Gain hands-on experience in creating, testing, and refining your own workflows tailored to specific business needs.

### Prerequisites

To follow this tutorial, you need access to an Oracle Private AI Agent Studio environment with the necessary permissions to use Template Gallery features and Agent Builder tools. You should also have access to at least one data file (such as a PDF) and an LLM configuration that is available in your environment.

> Note: Screenshots in this tutorial use example files and configurations for illustration purposes. When following along, use resources that are available in your environment.

## Task 1: Create an agent from the Template Gallery

The Template Gallery offers a curated collection of pre-built agentic templates designed to help you get started quickly with intelligent automation.

Templates may include workflows for tasks such as document summarization, meeting note extraction, content transformation, and more. You can browse, search, and import any template that fits your needs, customizing them as needed with minimal configuration.

![Main dashboard of Oracle Private AI Agent Studio with the left navigation panel expanded. The Template Gallery option under the Studio section is highlighted, and the Get Started page is displayed with pre-built agent options and a quick start guide on the right.](images/left_panel_template_gallery.png)

1. Open Oracle Private AI Agent Studio and log in. In the sidebar, click **Template Gallery**.

    ![Template Gallery screen displaying a list of template options, each with a description, last updated date, and an 'Import Flow' button. Templates include Draft Release Notes Generator, PDF to Blog Converter, Meeting Summary Item Extractor, Recruitment Optimizer, and Generate Product Pitch.](images/template_gallery.png)

    Here you will find all prebuilt workflows currently offered by Oracle Private AI Agent Studio.

2. For this tutorial, we will use the "PDF to Blog Converter" as an example, but you are encouraged to explore other templates based on your needs. Select a template to continue.

    ![Agent Builder workflow for a pdf-to-blog converter, showing nodes for File Upload, Prompt, Vllm (language model), Chat Input, and Chat Output connected in sequence. The File Upload and Chat Input nodes feed into the Prompt node, which sends its output to the Vllm node, and finally to the Chat Output node. Node configuration panels and connection points are visible.](images/pdf-to-blog.png)

3. The prebuilt workflow will be displayed and can be customized using a simple drag-and-drop interface, no code required. To help identify the workflow, you can change its name in the top right corner of the canvas. For this example, type a name such as “Blog Post Generator” or another descriptive name of your choice.

    ![Edit Details modal dialog open in Agent Builder, showing fields to edit the name and description of the custom flow. The background displays the workflow editor with nodes and connections, while the modal has options to cancel or save changes.](images/edit_details.png)

4. You are also able modify the workflow components to suit your needs. For instance, you can remove a node by selecting it and pressing Delete, and you can add a new node (such as an LLM or agent) by dragging it from the palette and configuring it as needed.

    ![Agent Builder workflow for pdf-to-blog showing the Vllm node highlighted with a red 'delete' label, indicating it is selected for deletion. Other nodes include File Upload, Prompt, Chat Input, and Chat Output, all connected in sequence.](images/pdf_to_blog_4a.png)

    ![Agent Builder workflow for pdf-to-blog showing an arrow from the OCI Agent component in the side panel to a newly added OCI Agent node in the workspace. The node's configuration field is highlighted, and it is connected in sequence after the Prompt node, replacing the previous Vllm node.](images/pdf_to_blog_4b.png)

    For any workflow, make sure you supply an LLM configuration name that matches one set up in your environment.
    Connect nodes by dragging from the output of one node to the input of another as instructed.

    ![Agent Builder workflow showing the nodes being connected. The output of the Prompt node is actively connected to the Prompt input of the OCI Agent node, indicated by highlighted connection points and an arrow. Other nodes include File Upload, Chat Input, and Chat Output.](images/pdf_to_blog_4c.png)

    ![Agent Builder workflow for pdf-to-blog structure showing fully connected nodes: File Upload and Chat Input feed into the Prompt node, which connects to the OCI Agent node, and then to the Chat Output node. All nodes are configured and linked in a sequential flow.](images/pdf_to_blog_4d.png)

5. Some templates are designed to process files as inputs, such as PDF files. If the template requires it, use the **Upload File** function, select your file, and choose it from the dropdown.

    ![Agent Builder workflow showing the File Upload node's dropdown expanded to select a file, with a PDF file highlighted. The workflow connects File Upload and Chat Input nodes to a Prompt node, which links to an OCI Agent node and then to a Chat Output node.](images/select_placeholder.png)

6. Click Publish to deploy your customized workflow.

    ![Publish Workflow confirmation dialog open in Agent Builder, asking the user to confirm publishing the '23ai Database New Features' workflow. The dialog has Cancel and Confirm buttons, overlaying the workflow editor with connected nodes for File Upload, Prompt, OCI Agent, and Chat Output.](images/publish_workflow.png)

## Task 2: Interact with the created workflow

After publishing the workflow, go to your workflow gallery. In the sidebar, click **My Custom Workflows**.

![My custom workflows screen displaying a search bar and a card for the 23ai Database New Features workflow, which contains a description, a label indicating it has been published and the last updated date. Buttons for delete, edit and run the workflow appears at the bottom.](images/custom_flows.png)

Select your workflow from the gallery. Here, you can edit, delete, or run your custom workflows. To proceed, click **Run Flow**.

![23ai Database New Features Chat screen with tabs for messages and chat history. The main chat area displays the prompt 'Star using your custom flow' with a message input field at the bottom containing 'How can I help you?'.](images/pdf_to_blog_chat_ui.png)

Interact with your workflow through the chat interface. Example query prompts will depend on your data source contents. For example, if your document is a product release guide, you could ask about new features described within. The workflow will provide responses based only on the information it has processed from your chosen file.

![Chat interface foe the '23ai Database New Features' custom workflow showing a user asking about the new data type added in Oracle Database 23ai and a response from the custom Flow answering the question. The main area displays messages and responses, with chat input available at the bottom.](images/pdf_to_blog_qa.png)

## (Optional) Task 3: Explore other templates

Explore additional templates in the Template Gallery to reinforce your learning and discover further use cases. Each template is immediately customizable and can be adapted to a variety of scenarios.

## Task 4: Explore the agent builder

The Agent Builder enables you to design, orchestrate, and automate complex processes by combining modular components, such as language models, data connectors, APIs, and specialized agents, without the need for extensive programming.

With the Agent Builder, you can visually construct workflows by connecting nodes that represent specific actions, tools, or data sources using a straightforward drag-and-drop interface. This feature allows you to build intelligent workflows using components like LLMs, chat agents, and data processing tools. You can also define agents that autonomously perform tasks, make decisions, or interact with systems based on your workflows.

Workflows created with the Agent Builder can be seamlessly integrated with enterprise systems, third-party services, cloud APIs, and databases. They are reusable and can easily be modified to meet varying business requirements.

The following table explores the various types of nodes you can use in the Agent Builder to create custom workflows. You may mix and match them to tailor workflows to your specific goals.

| Type | Description |
|--|--|
| Language Model | *vLLM*: Node leveraging the vLLM (virtualized Large Language Model) system for fast, efficient LLM inference. |
| Agents | - *vLLM Agent*: Node utilizing a vLLM instance to carry out instructions, answer questions, or facilitate complex workflows. - *OCI Agent*: Node connected to Oracle Cloud Infrastructure (OCI) services, enabling use of models served by Gen AI Services. |
| Tools | *MCP Server*: Specialized node for interfacing with AI models using the Model Context Protocol (MCP). (SSE Only) |
| Inputs | - *Chat Input*: Designed for conversational user input in a chat-based interface. - *Text Input*: Receives plain text input directly from the user. - *Prompt*: For defining or modifying textual instructions sent to a language model. |
| Outputs | - *Chat Output*: Renders or returns model/agent responses in a chat interface. |
| Data | - *Read CSV*: Imports and parses CSV files for batch or tabular data processing. - *File Upload*: Allows users to upload files for processing or analysis. - *SQL Query*: Executes SQL statements against databases; returns results for workflow use. |

## Task 5: Create a custom workflow

In this task you will create a simple workflow to gain hands-on experience with the Agent Builder interface and its capabilities.

1. **Open Oracle Private AI Agent Studio and log in.**
    In the sidebar, click **Agent Builder**.

    ![Main dashboard of Oracle Private AI Agent Studio with the left navigation panel expanded. The Agent Builder option under the Utilities section is highlighted, and the Get Started page is displayed with pre-built agent options and a quick start guide on the right.](images/left_panel_agent_builder.png)

    ![Agent Builder screen showing a components panel on the left with categories such as Language Model, Agents, Tools, Inputs, Outputs, and Data. The main workspace area is blank, and 'Playground' and 'Publish' buttons are in the upper right corner.](images/agent_builder.png)

2. Add nodes.

    On the left side of the canvas, you will find the available nodes. Drag an Agent node (such as OCI Agent or vLLM Agent) onto the canvas. Configure it with an LLM configuration name from your environment.

    ![Agent Builder screen showing step 2, adding an OCI Agent node. A red arrow curves from the OCI Agent option in the components panel on the left to a newly added OCI Agent node on the workspace. The node configuration panel displays fields for configuration, tools, custom instructions, prompt, and temperature.](images/step2.png)

    On the top left corner of the canvas type a name for the workflow, such as "Scientific Paper Summarizer".

3. Connect nodes.

    Repeat the process and add a **Chat Output** node. On the Chat Output node, click on the blue edge and drag it until it connects with the right edge of the OCI/vLLM Agent node edge, as shown below.

    ![Agent Builder screen showing step 3, adding and connecting a Chat Output node to the workflow. A red arrow connects the Message output of the OCI Agent node to the Message input of the Chat Output node, with both nodes visible and highlighted connection points.](images/step3a.png)

    If you need to remove a connection between two nodes, simply click the connecting line and press Delete on you keyboard.

    Add a **Chat Input** node as well, but do not connect it for now.

    ![Agent Builder screen showing an arrow from the Chat Input component in the left panel to a newly placed Chat Input node in the workspace. The workflow contains three nodes: Chat Input, OCI Agent, and Chat Output, with the OCI Agent connected to the Chat Output.](images/step3b.png)

4. Enrich prompts.

    As previously mentioned, the Prompt node allows you to enrich the instructions provided to the AI.

    Add a **Prompt** node and enter instructions in the text box. If you wish to add variable information, encapsulate it in curly braces; this will automatically add a connection edge to the node once saved. Example:

    ```bash
    Given the provided text, extract all key information and important details. Use this information to automatically generate a easy to understand summary.
    Provided text : {{user_input}}
    ```

    ![Agent Builder screen showing step 4a, adding a Prompt node to the workflow. A red arrow points from the Prompt component in the left panel to a newly created Prompt node placed between the Chat Input and OCI Agent nodes in the workspace. The Prompt node features a template input and save button.](images/step4a.png)

    ![Agent Builder screen showing step 4b, with a Prompt node added between the Chat Input and OCI Agent nodes. The Prompt node contains a filled-in template field describing instructions to generate an easy-to-understand summary, including a variable for user input.](images/step4b.png)

    ![Agent Builder screen showing step 4c, a canvas displaying a workflow with File Upload, Prompt, OCI Agent, and Chat Output nodes. The Prompt node receives input from both the File Upload and Chat Input nodes, and its output is connected to the Prompt input of the OCI Agent. Path connections and active connection points are highlighted in the workflow.](images/step4c.png)

    Connect the nodes as illustrated so that the Chat Input feeds into the Prompt, which feeds into the agent node, which connects to the Chat Output.

    ![Agent Builder screen showing step 4d, with the Chat Input node connected to the Prompt node, the Prompt node connected to the OCI Agent node, and the OCI Agent node connected to the Chat Output node. Arrows indicate the workflow sequence through all nodes, and the Prompt template field is populated with summary instructions and a user input variable.](images/step4d.png)

5. Save and test.

    Save the workflow by clicking the **Save** button in the top-right corner of the canvas. You can test the workflow before publishing it by clicking **Playground**. In the Playground, you may use test text or sample data relevant to your organization for input.

    ![Scientific Paper Summarizer custom flow screen showing a message that the new custom flow has been created. The main area prompts the user to start using the custom flow by typing a message, with options to start a new chat or go back to the builder. The chat input field is visible at the bottom.](images/step5a.png)

    ![Scientific Paper Summarizer custom flow test screen showing a user input and the Custom Flow Agent's response with a summary and key points about the data source used. The interface includes options to start a new chat or go back to the builder, and the chat input field is visible at the bottom.](images/step5b.png)

## (Optional) Task 6: Create your own custom workflow

Once comfortable, try designing a workflow of your own—tailor it to your data, business case, or automation scenario of interest.

## Summary

This concludes the current module. You now know how to use the Template Gallery to leverage pre-build workflows and hot to design your own custom workflows using the Agent Builder. These tools enable you to build, test and deploy advanced AI workflows tailored for your needs.

We hope this LiveLab has been illustrative and helpful to you in exploring and learning all of the features of Oracle Private AI Agent Studio. Explore additional modules for further discoveries and learning opportunities. You may now **proceed to the next lab**.

## Acknowledgements

- **Author** - Emilio Perez, Member of Technical Staff, Database Applied AI
- **Last Updated By/Date** - Emilio Perez - August 2025
