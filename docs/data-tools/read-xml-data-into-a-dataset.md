---
title: Lire les données XML dans un dataset
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6cceca336403bdd8907cf0e28e36387eb25a2402
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281784"
---
# <a name="read-xml-data-into-a-dataset"></a>Lire les données XML dans un dataset

ADO.NET fournit des méthodes simples pour travailler avec des données XML. Dans cette procédure pas à pas, vous allez créer une application Windows qui charge des données XML dans un DataSet. Le DataSet est ensuite affiché dans un <xref:System.Windows.Forms.DataGridView> contrôle. Enfin, un schéma XML basé sur le contenu du fichier XML est affiché dans une zone de texte.

## <a name="create-a-new-project"></a>Création d'un projet

Créez un projet d' **application Windows Forms** pour C# ou Visual Basic. Nommez le projet **ReadingXML**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Générer le fichier XML à lire dans le jeu de données

Étant donné que cette procédure pas à pas porte sur la lecture de données XML dans un DataSet, le contenu d’un fichier XML est fourni.

1. Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.

2. Sélectionnez **fichier XML**, nommez le fichier **authors.xml**, puis sélectionnez **Ajouter**.

   Le fichier XML se charge dans le concepteur et est prêt pour la modification.

3. Collez les données XML suivantes dans l’éditeur sous la déclaration XML :

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

4. Dans le menu **fichier** , sélectionnez **Enregistrer authors.xml**.

## <a name="create-the-user-interface"></a>Créer l’interface utilisateur

L’interface utilisateur de cette application se compose des éléments suivants :

- <xref:System.Windows.Forms.DataGridView>Contrôle qui affiche le contenu du fichier XML sous forme de données.

- <xref:System.Windows.Forms.TextBox>Contrôle qui affiche le schéma XML pour le fichier XML.

- Deux <xref:System.Windows.Forms.Button> contrôles.

  - Un bouton lit le fichier XML dans le jeu de données et l’affiche dans le <xref:System.Windows.Forms.DataGridView> contrôle.

  - Un deuxième bouton extrait le schéma du DataSet et, via un, l' <xref:System.IO.StringWriter> affiche dans le <xref:System.Windows.Forms.TextBox> contrôle.

### <a name="to-add-controls-to-the-form"></a>Pour ajouter des contrôles au formulaire

1. Ouvrez `Form1` en mode Design.

2. À partir de la **boîte à outils**, faites glisser les contrôles suivants sur le formulaire :

    - Un <xref:System.Windows.Forms.DataGridView> contrôle

    - Un <xref:System.Windows.Forms.TextBox> contrôle

    - Deux <xref:System.Windows.Forms.Button> contrôles

3. Définissez les propriétés suivantes :

    |Contrôler|Propriété|Paramètre|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**BarreDéfilement**|**Barr**|
    |`Button1`|**Nom**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**Nom**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Créer le DataSet qui reçoit les données XML

Dans cette étape, vous allez créer un nouveau jeu de données nommé `authors` . Pour plus d’informations sur les datasets, consultez [outils de jeu de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

1. Dans **Explorateur de solutions**, sélectionnez le fichier source pour **Form1**, puis sélectionnez le bouton **Concepteur de vues** dans la barre d’outils **Explorateur de solutions** .

2. À partir de l' [onglet données de la boîte à outils](../ide/reference/toolbox-data-tab.md), faites glisser un **DataSet** sur **Form1**.

3. Dans la boîte de dialogue **Ajouter un DataSet** , sélectionnez **DataSet non typé**, puis cliquez sur **OK**.

     **DataSet1** est ajouté à la barre d’état des composants.

4. Dans la fenêtre **Propriétés** , définissez le **nom** et les <xref:System.Data.DataSet.DataSetName%2A> Propriétés de `AuthorsDataSet` .

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Créer le gestionnaire d’événements pour lire le fichier XML dans le jeu de données

Le bouton **lire XML** lit le fichier XML dans le jeu de données. Il définit ensuite les propriétés du <xref:System.Windows.Forms.DataGridView> contrôle qui le lient au DataSet.

1. Dans **Explorateur de solutions**, sélectionnez **Form1**, puis cliquez sur le bouton **Concepteur de vues** dans la barre d’outils **Explorateur de solutions** .

2. Sélectionnez le bouton **lire XML** .

     L' **éditeur de code** s’ouvre au niveau du `ReadXmlButton_Click` Gestionnaire d’événements.

3. Tapez le code suivant dans le `ReadXmlButton_Click` Gestionnaire d’événements :

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4. Dans le `ReadXMLButton_Click` Code du gestionnaire d’événements, remplacez l' `filepath =` entrée par le chemin d’accès correct.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Créer le gestionnaire d’événements pour afficher le schéma dans la zone de texte

Le bouton **afficher le schéma** crée un <xref:System.IO.StringWriter> objet qui est rempli avec le schéma et s’affiche dans le <xref:System.Windows.Forms.TextBox> contrôle.

1. Dans **Explorateur de solutions**, sélectionnez **Form1**, puis cliquez sur le bouton **Concepteur de vues** .

2. Sélectionnez le bouton **afficher le schéma** .

     L' **éditeur de code** s’ouvre au niveau du `ShowSchemaButton_Click` Gestionnaire d’événements.

3. Collez le code suivant dans le gestionnaire d’événements `ShowSchemaButton_Click`.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>Tester le formulaire

Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.

1. Appuyez sur **F5** pour exécuter l’application.

2. Sélectionnez le bouton **lire XML** .

     Le DataGridView affiche le contenu du fichier XML.

3. Sélectionnez le bouton **afficher le schéma** .

     La zone de texte affiche le schéma XML pour le fichier XML.

## <a name="next-steps"></a>Étapes suivantes

Cette procédure pas à pas vous apprend les bases de la lecture d’un fichier XML dans un jeu de données, ainsi que la création d’un schéma basé sur le contenu du fichier XML. Voici quelques tâches que vous pouvez effectuer ensuite :

- Modifiez les données dans le DataSet et Réécrivez-les en tant que XML. Pour plus d'informations, consultez <xref:System.Data.DataSet.WriteXml%2A>.

- Modifiez les données dans le DataSet et écrivez-les dans une base de données.

## <a name="see-also"></a>Voir aussi

- [Accéder aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Outils XML dans Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
