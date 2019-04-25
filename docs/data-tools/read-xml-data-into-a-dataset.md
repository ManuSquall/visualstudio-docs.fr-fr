---
title: Lire les données XML dans un dataset
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fa0472ae7ad7200ead372057f1dd778c077f764e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076027"
---
# <a name="read-xml-data-into-a-dataset"></a>Lire les données XML dans un dataset

ADO.NET fournit des méthodes simples pour travailler avec des données XML. Dans cette procédure pas à pas, vous créez une application Windows qui charge des données XML dans un jeu de données. Le jeu de données est ensuite affichée dans un <xref:System.Windows.Forms.DataGridView> contrôle. Enfin, un schéma XML en fonction du contenu du fichier XML s’affiche dans une zone de texte.

## <a name="create-a-new-project"></a>Créer un nouveau projet

Créer un nouveau **Windows Forms application** projet pour soit C# ou Visual Basic. Nommez le projet **ReadingXML**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Générer le fichier XML à lire dans le jeu de données

Étant donné que cette procédure pas à pas se concentre sur la lecture de données XML dans un dataset, le contenu d’un fichier XML est fourni.

1. Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.

2. Sélectionnez **fichier XML**, nommez le fichier **authors.xml**, puis sélectionnez **ajouter**.

   Le fichier XML chargé dans le concepteur et est prêt pour la modification.

3. Collez les données XML suivantes dans l’éditeur, sous la déclaration XML :

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

4. Sur le **fichier** menu, sélectionnez **enregistrer authors.xml**.

## <a name="create-the-user-interface"></a>Créer l’interface utilisateur

L’interface utilisateur pour cette application se compose des éléments suivants :

- Un <xref:System.Windows.Forms.DataGridView> contrôle qui affiche le contenu du fichier XML sous forme de données.

- Un <xref:System.Windows.Forms.TextBox> contrôle qui affiche le schéma XML pour le fichier XML.

- Deux <xref:System.Windows.Forms.Button> contrôles.

    - Un bouton lit le fichier XML dans le jeu de données et l’affiche dans le <xref:System.Windows.Forms.DataGridView> contrôle.

    - Un deuxième bouton extrait le schéma du jeu de données et via un <xref:System.IO.StringWriter> affiche dans le <xref:System.Windows.Forms.TextBox> contrôle.

### <a name="to-add-controls-to-the-form"></a>Pour ajouter des contrôles au formulaire

1. Ouvrez `Form1` en mode design.

2. À partir de la **boîte à outils**, faites glisser les contrôles suivants sur le formulaire :

    - Un seul <xref:System.Windows.Forms.DataGridView> contrôle

    - Un seul <xref:System.Windows.Forms.TextBox> contrôle

    - Deux <xref:System.Windows.Forms.Button> contrôles

3. Définissez les propriétés suivantes :

    |Contrôle|Propriété|Paramètre|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**ScrollBars**|**Vertical**|
    |`Button1`|**Name**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**Name**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Créer le jeu de données qui reçoit les données XML

Dans cette étape, vous créez un nouveau dataset appelé `authors`. Pour plus d’informations sur les jeux de données, consultez [outils de Dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

1. Dans **l’Explorateur de solutions**, sélectionnez le fichier source pour **Form1**, puis sélectionnez le **Concepteur de vue** bouton sur le **l’Explorateur de solutions** barre d’outils.

2. À partir de la [boîte à outils, onglet données](../ide/reference/toolbox-data-tab.md), faites glisser un **DataSet** sur **Form1**.

3. Dans le **ajouter un Dataset** boîte de dialogue, sélectionnez **dataset non typé**, puis sélectionnez **OK**.

     **DataSet1** est ajouté à la barre d’état du composant.

4. Dans le **propriétés** fenêtre, définissez la **nom** et <xref:System.Data.DataSet.DataSetName%2A> propriétés pour`AuthorsDataSet`.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Créer le Gestionnaire d’événements pour lire le fichier XML dans le jeu de données

Le **lire XML** bouton lit le fichier XML dans le jeu de données. Il définit ensuite les propriétés sur le <xref:System.Windows.Forms.DataGridView> contrôle qui le lient au jeu de données.

1. Dans **l’Explorateur de solutions**, sélectionnez **Form1**, puis sélectionnez le **Concepteur de vue** bouton sur le **l’Explorateur de solutions** barre d’outils.

2. Sélectionnez le **lire XML** bouton.

     Le **éditeur de Code** s’ouvre à la `ReadXmlButton_Click` Gestionnaire d’événements.

3. Tapez le code suivant dans le `ReadXmlButton_Click` Gestionnaire d’événements :

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4. Dans le `ReadXMLButton_Click` code de gestionnaire d’événements, modification du `filepath =` entrée pour le chemin correct.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Créer le Gestionnaire d’événements pour afficher le schéma dans la zone de texte

Le **Afficher schéma** bouton crée un <xref:System.IO.StringWriter> objet qui est rempli avec le schéma et est affiché dans le <xref:System.Windows.Forms.TextBox>contrôle.

1. Dans **l’Explorateur de solutions**, sélectionnez **Form1**, puis sélectionnez le **Concepteur de vue** bouton.

2. Sélectionnez le **Afficher schéma** bouton.

     Le **éditeur de Code** s’ouvre à la `ShowSchemaButton_Click` Gestionnaire d’événements.

3. Collez le code suivant dans le gestionnaire d’événements `ShowSchemaButton_Click`.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>Le formulaire de test

Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.

1. Sélectionnez **F5** pour exécuter l’application.

2. Sélectionnez le **lire XML** bouton.

     Le DataGridView affiche le contenu du fichier XML.

3. Sélectionnez le **Afficher schéma** bouton.

     La zone de texte affiche le schéma XML pour le fichier XML.

## <a name="next-steps"></a>Étapes suivantes

Cette procédure pas à pas vous enseigne les principes fondamentaux de la lecture d’un fichier XML dans un jeu de données, ainsi que la création d’un schéma en fonction du contenu du fichier XML. Voici quelques tâches que vous pouvez effectuer ensuite :

- Modifier les données dans le jeu de données et les enregistrer à nouveau au format XML. Pour plus d'informations, consultez <xref:System.Data.DataSet.WriteXml%2A>.

- Modifier les données dans le jeu de données et écrire sur une base de données.

## <a name="see-also"></a>Voir aussi

- [Accéder aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Outils XML dans Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)