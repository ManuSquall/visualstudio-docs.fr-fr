---
title: Lire des données XML dans un dataset | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b858a6c513c1b9e1caa4f17c1bd8af067de47365
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114897"
---
# <a name="read-xml-data-into-a-dataset"></a>Lire les données XML dans un dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ADO.NET fournit des méthodes simples pour travailler avec des données XML. Dans cette procédure pas à pas, vous créez une application Windows qui charge des données XML dans un jeu de données. Le jeu de données est ensuite affichée dans un <xref:System.Windows.Forms.DataGridView> contrôle. Enfin, un schéma XML en fonction du contenu du fichier XML s’affiche dans une zone de texte.  
  
 Cette procédure pas à pas se compose de cinq étapes principales :  
  
1. Création d’un projet  
  
2. Création d’un fichier XML à lire dans le jeu de données  
  
3. Création de l’interface utilisateur  
  
4. Création du jeu de données, la lecture du fichier XML et l’affichage dans un <xref:System.Windows.Forms.DataGridView> contrôle  
  
5. Ajout du code pour afficher le schéma XML basé sur le fichier XML dans un <xref:System.Windows.Forms.TextBox> contrôle  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l’aide selon vos paramètres actifs ou de l’édition que vous utilisez. Pour modifier vos paramètres, sur le **outils** menu, sélectionnez**importation et exportation de paramètres**. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-new-project"></a>Créer un nouveau projet  
 Dans cette étape, vous créez un projet Visual Basic ou Visual c# qui contient cette procédure pas à pas.  
  
#### <a name="to-create-the-new-windows-project"></a>Pour créer un projet Windows  
  
1. Sur le **fichier** menu, créez un nouveau projet.  
  
2. Attribuez un nom au projet `ReadingXML`.  
  
3. Sélectionnez **Windows Application**, puis sélectionnez **OK**. Pour plus d’informations, consultez [les Applications clientes](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Le **ReadingXML** projet est créé et ajouté à **l’Explorateur de solutions**.  
  
## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Générer le fichier XML à lire dans le jeu de données  
 Étant donné que cette procédure pas à pas se concentre sur la lecture de données XML dans un dataset, le contenu d’un fichier XML est fourni.  
  
#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Pour créer le fichier XML qui sera lu dans le jeu de données  
  
1. Sur le **projet** menu, sélectionnez**ajouter un nouvel élément**.  
  
2. Sélectionnez **fichier XML**, nommez le fichier `authors.xml`, puis sélectionnez **ajouter**.  
  
     Le fichier XML chargé dans le concepteur et est prêt pour la modification.  
  
3. Collez le code suivant dans l’éditeur, sous la déclaration XML :  
  
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
  
4. Sur le **fichier** menu, sélectionnez**enregistrer authors.xml**.  
  
## <a name="create-the-user-interface"></a>Créer l’interface utilisateur  
 L’interface utilisateur pour cette application se compose des éléments suivants :  
  
- Un <xref:System.Windows.Forms.DataGridView> contrôle qui affiche le contenu du fichier XML sous forme de données.  
  
- Un <xref:System.Windows.Forms.TextBox> contrôle qui affiche le schéma XML pour le fichier XML.  
  
- Deux <xref:System.Windows.Forms.Button> contrôles.  
  
    - Un bouton lit le fichier XML dans le jeu de données et l’affiche dans le <xref:System.Windows.Forms.DataGridView> contrôle.  
  
    - Un deuxième bouton extrait le schéma du jeu de données et via un <xref:System.IO.StringWriter> affiche dans le <xref:System.Windows.Forms.TextBox> contrôle.  
  
#### <a name="to-add-controls-to-the-form"></a>Pour ajouter des contrôles au formulaire  
  
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
  
## <a name="create-the-dataset-thatreceives-the-xml-data"></a>Créer le jeu de données thatreceives les données XML  
 Dans cette étape, vous créez un nouveau dataset appelé `authors`. Pour plus d’informations sur les jeux de données, consultez [outils de Dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>Pour créer un nouveau jeu de données qui reçoit les données XML  
  
1. Dans **l’Explorateur de solutions**, sélectionnez le fichier source pour **Form1**, puis sélectionnez le **Concepteur de vue** bouton sur le **l’Explorateur de solutions** barre d’outils.  
  
2. À partir de la [boîte à outils, onglet données](../ide/reference/toolbox-data-tab.md), faites glisser un **DataSet** sur **Form1**.  
  
3. Dans le **ajouter un Dataset** boîte de dialogue, sélectionnez **dataset non typé**, puis sélectionnez **OK**.  
  
     **DataSet1** est ajouté à la barre d’état du composant.  
  
4. Dans le **propriétés** fenêtre, définissez la **nom** et <xref:System.Data.DataSet.DataSetName%2A> propriétés pour`AuthorsDataSet`.  
  
## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Créer le Gestionnaire d’événements pour lire le fichier XML dans le jeu de données  
 Le **lire XML** bouton lit le fichier XML dans le jeu de données. Il définit ensuite les propriétés sur le <xref:System.Windows.Forms.DataGridView> contrôle qui le lient au jeu de données.  
  
#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>Pour ajouter du code au gestionnaire d’événements ReadXmlButton_Click  
  
1. Dans **l’Explorateur de solutions**, sélectionnez **Form1**, puis sélectionnez le **Concepteur de vue** bouton sur le **l’Explorateur de solutions** barre d’outils.  
  
2. Sélectionnez le **lire XML** bouton.  
  
     Le **éditeur de Code** s’ouvre à la `ReadXmlButton_Click` Gestionnaire d’événements.  
  
3. Tapez le code suivant dans le `ReadXmlButton_Click` Gestionnaire d’événements :  
  
     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]  
  
4. Dans le `ReadXMLButton_Click` code de gestionnaire d’événements, modification du `filepath =` entrée pour le chemin correct.  
  
## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Créer le Gestionnaire d’événements pour afficher le schéma dans la zone de texte  
 Le **Afficher schéma** bouton crée un <xref:System.IO.StringWriter> objet qui est rempli avec le schéma et est affiché dans le <xref:System.Windows.Forms.TextBox>contrôle.  
  
#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>Pour ajouter du code au gestionnaire d’événements ShowSchemaButton_Click  
  
1. Dans **l’Explorateur de solutions**, sélectionnez **Form1**, puis sélectionnez le **Concepteur de vue** bouton.  
  
2. Sélectionnez le **Afficher schéma** bouton.  
  
     Le **éditeur de Code** s’ouvre à la `ShowSchemaButton_Click` Gestionnaire d’événements.  
  
3. Tapez le code suivant dans le `ShowSchemaButton_Click` Gestionnaire d’événements.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]  
  
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
 [Procédures pas à pas relatives aux données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Outils XML dans Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)