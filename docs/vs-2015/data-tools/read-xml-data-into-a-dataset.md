---
title: Lire des données XML dans un jeu de données | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c34fb87c02ff60d9b28c43130d6fbf3a12e70349
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652904"
---
# <a name="read-xml-data-into-a-dataset"></a>Lire les données XML dans un dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ADO.NET fournit des méthodes simples pour travailler avec des données XML. Dans cette procédure pas à pas, vous allez créer une application Windows qui charge des données XML dans un DataSet. Le DataSet est ensuite affiché dans un contrôle de <xref:System.Windows.Forms.DataGridView>. Enfin, un schéma XML basé sur le contenu du fichier XML est affiché dans une zone de texte.

 Cette procédure pas à pas se compose de cinq étapes principales :

1. Création d’un nouveau projet

2. Création d’un fichier XML à lire dans le jeu de données

3. Création de l’interface utilisateur

4. Création du DataSet, lecture du fichier XML et affichage dans un contrôle de <xref:System.Windows.Forms.DataGridView>

5. Ajout de code pour afficher le schéma XML en fonction du fichier XML dans un contrôle de <xref:System.Windows.Forms.TextBox>

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l’aide en fonction de vos paramètres actifs ou de l’édition que vous utilisez. Pour modifier vos paramètres, dans le menu **Outils** , sélectionnez**paramètres d’importation et d’exportation**. Pour plus d’informations, consultez [Paramètres Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-new-project"></a>Créer un projet
 Dans cette étape, vous créez un Visual Basic ou un C# projet visuel qui contient cette procédure pas à pas.

#### <a name="to-create-the-new-windows-project"></a>Pour créer un projet Windows

1. Dans le menu **fichier** , créez un nouveau projet.

2. Attribuez un nom au projet `ReadingXML`.

3. Sélectionnez **application Windows**, puis cliquez sur **OK**. Pour plus d’informations, consultez [applications clientes](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Le projet **ReadingXML** est créé et ajouté à **Explorateur de solutions**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Générer le fichier XML à lire dans le jeu de données
 Étant donné que cette procédure pas à pas porte sur la lecture de données XML dans un DataSet, le contenu d’un fichier XML est fourni.

#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Pour créer le fichier XML qui sera lu dans le jeu de données

1. Dans le menu **projet** , sélectionnez**Ajouter un nouvel élément**.

2. Sélectionnez **fichier XML**, nommez le fichier `authors.xml`, puis sélectionnez **Ajouter**.

     Le fichier XML se charge dans le concepteur et est prêt pour la modification.

3. Collez le code suivant dans l’éditeur sous la déclaration XML :

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

4. Dans le menu **fichier** , sélectionnez**Enregistrer Authors. xml**.

## <a name="create-the-user-interface"></a>Créer l’interface utilisateur
 L’interface utilisateur de cette application se compose des éléments suivants :

- Contrôle <xref:System.Windows.Forms.DataGridView> qui affiche le contenu du fichier XML sous forme de données.

- Contrôle <xref:System.Windows.Forms.TextBox> qui affiche le schéma XML pour le fichier XML.

- Deux contrôles <xref:System.Windows.Forms.Button>.

  - Un bouton lit le fichier XML dans le jeu de données et l’affiche dans le contrôle <xref:System.Windows.Forms.DataGridView>.

  - Un deuxième bouton extrait le schéma du DataSet et, via une <xref:System.IO.StringWriter> l’affiche dans le contrôle <xref:System.Windows.Forms.TextBox>.

#### <a name="to-add-controls-to-the-form"></a>Pour ajouter des contrôles au formulaire

1. Ouvrez `Form1` en mode Design.

2. À partir de la **boîte à outils**, faites glisser les contrôles suivants sur le formulaire :

    - Un contrôle <xref:System.Windows.Forms.DataGridView>

    - Un contrôle <xref:System.Windows.Forms.TextBox>

    - Deux contrôles <xref:System.Windows.Forms.Button>

3. Définissez les propriétés suivantes :

    |Contrôle|Property|Paramètre|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**ScrollBars**|**Vertical**|
    |`Button1`|**Nom**|`ReadXmlButton`|
    ||**Texte**|`Read XML`|
    |`Button2`|**Nom**|`ShowSchemaButton`|
    ||**Texte**|`Show Schema`|

## <a name="create-the-dataset-thatreceives-the-xml-data"></a>Créer le DataSet thatreceives les données XML
 Dans cette étape, vous créez un jeu de données nommé `authors`. Pour plus d’informations sur les datasets, consultez [outils de jeu de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>Pour créer un nouveau jeu de données qui reçoit les données XML

1. Dans **Explorateur de solutions**, sélectionnez le fichier source pour **Form1**, puis sélectionnez le bouton **Concepteur de vues** dans la barre d’outils **Explorateur de solutions** .

2. À partir de l' [onglet données de la boîte à outils](../ide/reference/toolbox-data-tab.md), faites glisser un **DataSet** sur **Form1**.

3. Dans la boîte de dialogue **Ajouter un DataSet** , sélectionnez **DataSet non typé**, puis cliquez sur **OK**.

     **DataSet1** est ajouté à la barre d’état des composants.

4. Dans la fenêtre **Propriétés** , définissez les propriétés **Name** et <xref:System.Data.DataSet.DataSetName%2A> pour `AuthorsDataSet`.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Créer le gestionnaire d’événements pour lire le fichier XML dans le jeu de données
 Le bouton **lire XML** lit le fichier XML dans le jeu de données. Il définit ensuite les propriétés sur le contrôle <xref:System.Windows.Forms.DataGridView> qui le lient au DataSet.

#### <a name="to-add-code-to-the-readxmlbutton_click-event-handler"></a>Pour ajouter du code au gestionnaire d’événements ReadXmlButton_Click

1. Dans **Explorateur de solutions**, sélectionnez **Form1**, puis cliquez sur le bouton **Concepteur de vues** dans la barre d’outils **Explorateur de solutions** .

2. Sélectionnez le bouton **lire XML** .

     L' **éditeur de code** s’ouvre au niveau du gestionnaire d’événements `ReadXmlButton_Click`.

3. Tapez le code suivant dans le gestionnaire d’événements `ReadXmlButton_Click` :

     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]

4. Dans le `ReadXMLButton_Click` code du gestionnaire d’événements, remplacez l’entrée `filepath =` par le chemin d’accès correct.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Créer le gestionnaire d’événements pour afficher le schéma dans la zone de texte
 Le bouton **afficher le schéma** crée un objet <xref:System.IO.StringWriter> qui est rempli avec le schéma et s’affiche dans le <xref:System.Windows.Forms.TextBox>control.

#### <a name="to-add-code-to-the-showschemabutton_click-event-handler"></a>Pour ajouter du code au gestionnaire d’événements ShowSchemaButton_Click

1. Dans **Explorateur de solutions**, sélectionnez **Form1**, puis cliquez sur le bouton **Concepteur de vues** .

2. Sélectionnez le bouton **afficher le schéma** .

     L' **éditeur de code** s’ouvre au niveau du gestionnaire d’événements `ShowSchemaButton_Click`.

3. Tapez le code suivant dans le gestionnaire d’événements `ShowSchemaButton_Click`.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]

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
 [Procédures pas à pas](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) relatives à [l’accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [préparation de votre application pour la réception](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [des outils XML de données dans Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
