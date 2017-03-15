---
title: "Proc&#233;dure pas &#224; pas&#160;: lecture des donn&#233;es XML dans un groupe de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "données (Visual Studio), lire dans les fichiers XML"
  - "accès aux données (Visual Studio), données XML"
  - "groupes de données (Visual Basic), lire les données XML"
  - "lire des données, fichiers XML"
  - "lire des fichiers, XML"
  - "lire des données XML"
  - "XML (Visual Studio), lire"
  - "documents XML, lire"
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: lecture des donn&#233;es XML dans un groupe de donn&#233;es
ADO.NET offre des méthodes simples pour l'utilisation des données XML.  Dans le cadre de cette procédure pas à pas, vous allez créer une application Windows qui va charger des données XML dans un groupe de données.  Le groupe de données sera affiché dans un <xref:System.Windows.Forms.DataGridView>.  À la fin, un schéma XML basé sur le contenu du fichier XML sera affiché dans une zone de texte.  
  
 Cette procédure pas à pas se compose de cinq étapes principales :  
  
1.  Création d'un nouveau projet.  
  
2.  Création d'un fichier XML à lire dans le groupe de données.  
  
3.  Création de l'interface utilisateur.  
  
4.  Création du groupe de données, lecture du fichier XML et affichage de celui\-ci dans un contrôle <xref:System.Windows.Forms.DataGridView>.  
  
5.  Ajout du code permettant d'afficher le schéma XML basé sur le fichier XML dans un contrôle <xref:System.Windows.Forms.TextBox>.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Création d'un projet  
 Dans cette étape, vous créerez un projet Visual Basic ou Visual C\# qui contiendra cette procédure pas à pas.  
  
#### Pour créer le nouveau projet Windows  
  
1.  Dans le menu **Fichier**, créez un nouveau projet.  
  
2.  Nommez le projet `ReadingXML`.  
  
3.  Sélectionnez **Application Windows**, puis cliquez sur **OK**.  Pour plus d'informations, consultez [Applications clientes](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Le projet **ReadingXML** est créé et ajouté à l'Explorateur de solutions.  
  
## Création du fichier XML qui sera lu dans le groupe de données  
 Cette procédure traite de la lecture de données XML dans un groupe de données. Le contenu d'un fichier XML vous est donc proposé.  
  
#### Pour créer le fichier XML qui sera lu dans le groupe de données  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
2.  Sélectionnez **Fichier XML**, nommez le fichier `authors.xml` et cliquez **Ajouter**.  
  
     Le fichier XML est chargé dans le concepteur et prêt pour la modification.  
  
3.  Collez le code suivant dans l'éditeur, sous la déclaration XML :  
  
    ```xml  
    <Authors_Table>  
      <authors>  
        <au_id>172-32-1176</au_id>  
        <au_lname>White</au_lname>  
        <au_fname>Johnson</au_fname>  
        <phone>408 496-7223</phone>  
        <address>10932 Bigge Rd.</address>  
        <city>Menlo Park</city>  
        <state>CA</state>  
        <zip>94025</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>213-46-8915</au_id>  
        <au_lname>Green</au_lname>  
        <au_fname>Margie</au_fname>  
        <phone>415 986-7020</phone>  
        <address>309 63rd St. #411</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94618</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>238-95-7766</au_id>  
        <au_lname>Carson</au_lname>  
        <au_fname>Cheryl</au_fname>  
        <phone>415 548-7723</phone>  
        <address>589 Darwin Ln.</address>  
        <city>Berkeley</city>  
        <state>CA</state>  
        <zip>94705</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>267-41-2394</au_id>  
        <au_lname>Hunter</au_lname>  
        <au_fname>Anne</au_fname>  
        <phone>408 286-2428</phone>  
        <address>22 Cleveland Av. #14</address>  
        <city>San Jose</city>  
        <state>CA</state>  
        <zip>95128</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>274-80-9391</au_id>  
        <au_lname>Straight</au_lname>  
        <au_fname>Dean</au_fname>  
        <phone>415 834-2919</phone>  
        <address>5420 College Av.</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94609</zip>  
        <contract>true</contract>  
      </authors>  
    </Authors_Table>  
    ```  
  
4.  Dans le menu **Fichier**, pointez sur **Enregistrer authors.xml**.  
  
## Création de l'interface utilisateur  
 Pour cette application, l'interface utilisateur se composera des éléments suivants :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> qui affichera le contenu du fichier XML sous la forme de données ;  
  
-   un contrôle <xref:System.Windows.Forms.TextBox> qui affichera le schéma XML du fichier XML ;  
  
-   deux contrôles <xref:System.Windows.Forms.Button> ;  
  
    -   le premier bouton lit le fichier XML en le plaçant dans le groupe de données et l'affiche dans le contrôle <xref:System.Windows.Forms.DataGridView> ;  
  
    -   le deuxième bouton extrait le schéma du groupe de données et l'affiche dans le contrôle <xref:System.Windows.Forms.TextBox> via un <xref:System.IO.StringWriter>.  
  
#### Pour ajouter des contrôles au formulaire  
  
1.  Ouvrez `Form1` en mode Design.  
  
2.  À partir de la **boîte à outils**, faites glisser les contrôles suivants jusqu'au formulaire :  
  
    -   Un contrôle <xref:System.Windows.Forms.DataGridView>  
  
    -   Un contrôle <xref:System.Windows.Forms.TextBox>  
  
    -   Deux contrôles <xref:System.Windows.Forms.Button>  
  
3.  Définissez les propriétés suivantes :  
  
    |Contrôle|Propriété|Paramètre|  
    |--------------|---------------|---------------|  
    |`TextBox1`|**Multiline**|`true`|  
    ||**ScrollBars**|**Vertical**|  
    |`Button1`|**Nom**|`ReadXmlButton`|  
    ||**Texte**|`Lire XML`|  
    |`Button2`|**Nom**|`ShowSchemaButton`|  
    ||**Texte**|`Afficher schéma`|  
  
## Création du groupe de données qui recevra les données XML  
 Au cours de la procédure suivante, vous allez créer un nouveau groupe de données appelé `authors`.  Pour plus d'informations sur les groupes de données, consultez [Utilisation de groupes de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### Pour créer un nouveau groupe de données qui recevra les données XML  
  
1.  Avec le fichier source de **Form1** sélectionné dans l'**Explorateur de solutions**, cliquez sur le bouton **Concepteur de vues** de la barre d'outils de l'**Explorateur de solutions**.  
  
2.  Dans l'[Boîte à outils, Onglet Données](../ide/reference/toolbox-data-tab.md), faites glisser un **DataSet** jusqu'à **Form1**.  
  
3.  Sélectionnez **groupe de données non typé** dans la boîte de dialogue d' **Ajoutez le groupe de données** , puis cliquez sur **OK**.  
  
     **DataSet1** est ajouté à la barre d'état des composants.  
  
4.  Dans la fenêtre **Propriétés**, affectez aux propriétés **Name** et <xref:System.Data.DataSet.DataSetName%2A> la valeur `AuthorsDataSet`.  
  
## Création du gestionnaire d'événements pour lire les données XML dans le groupe de données  
 Le bouton **Lire XML** lit le fichier XML dans le groupe de données et définit dans le contrôle <xref:System.Windows.Forms.DataGridView> les propriétés qui le lient au groupe de données.  
  
#### Pour ajouter le code au gestionnaire d'événements ReadXmlButton\_Click  
  
1.  Sélectionnez **Form1** dans l'**Explorateur de solutions** et cliquez sur le bouton **Concepteur de vues** dans la barre d'outils de l'**Explorateur de solutions**.  
  
2.  Double\-cliquez sur le bouton **Lire XML**.  
  
     L'**Éditeur de code** s'ouvre au gestionnaire d'événements `ReadXmlButton_Click`.  
  
3.  Tapez le code suivant dans le gestionnaire d'événements `ReadXmlButton_Click` :  
  
     [!code-cs[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]  
  
4.  Dans le code du gestionnaire d'événements `ReadXMLButton_Click`, remplacez l'entrée `filepath =` par le chemin d'accès correct.  
  
## Création du gestionnaire d'événements pour afficher le schéma dans le contrôle Textbox  
 Le bouton **Afficher schéma** crée un objet <xref:System.IO.StringWriter> rempli par le schéma et affiché dans <xref:System.Windows.Forms.TextBox>.  
  
#### Pour ajouter le code au gestionnaire d'événements ShowSchemaButton\_Click  
  
1.  Sélectionnez **Form1** dans l'**Explorateur de solutions** et cliquez sur le bouton **Concepteur de vues**.  
  
2.  Double\-cliquez sur le bouton **Afficher schéma**.  
  
     L'**Éditeur de code** s'ouvre au gestionnaire d'événements `ShowSchemaButton_Click`.  
  
3.  Tapez le code suivant dans le gestionnaire d'événements `ShowSchemaButton_Click`.  
  
     [!code-cs[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]  
  
## Test  
 Vous pouvez à présent tester le formulaire afin de vous assurer qu'il se comporte comme prévu.  
  
#### Pour tester le formulaire  
  
1.  Appuyez sur F5 pour exécuter l'application.  
  
2.  Cliquez sur le bouton **Lire XML**.  
  
     Le DataGridView affiche le contenu du fichier XML.  
  
3.  Cliquez sur le bouton **Afficher schéma**.  
  
     La zone de texte affiche le schéma XML pour le fichier XML.  
  
## Étapes suivantes  
 Cette procédure décrit les principes de base de la lecture d'un fichier XML dans un groupe de données et de la création d'un schéma basé sur le contenu du fichier XML.  Vous devrez peut\-être ensuite exécuter les opérations suivantes :  
  
-   Éditer les données dans le groupe de données et les enregistrer à nouveau au format XML.  Pour plus d'informations, consultez <xref:System.Data.DataSet.WriteXml%2A>.  
  
-   Éditer les données dans le groupe de données et les enregistrer dans une base de données.  Pour plus d'informations, consultez [Enregistrement des données](../data-tools/saving-data.md).  
  
## Voir aussi  
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Outils XML dans Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)