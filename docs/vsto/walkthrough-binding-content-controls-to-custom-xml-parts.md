---
title: 'Procédure pas à pas : Lier des contrôles de contenu à des parties XML personnalisées'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PlainTextContentControl, binding to a custom XML part
- custom XML parts, binding to content controls
- content controls [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], content controls
- DropDownListContentControl, binding items to a custom XML part
- DatePickerContentControl, binding to a custom XML part
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52366cc268335df98da53701e5cde283c67a022d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438703"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>Procédure pas à pas : Lier des contrôles de contenu à des parties XML personnalisées
  Cette procédure pas à pas montre comment lier les contrôles de contenu d'une personnalisation au niveau du document pour Word aux données XML stockées dans le document.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word vous permet de stocker des données XML, nommées *des parties XML personnalisées*, dans un document. Vous pouvez contrôler l'affichage de ces données en liant les contrôles de contenu aux éléments d'une partie XML personnalisée. L'exemple de document de cette procédure pas à pas affiche les informations sur les employés qui sont stockées dans une partie XML personnalisée. Lorsque vous ouvrez le document, les contrôles de contenu affichent les valeurs des éléments XML. Les modifications que vous apportez au texte des contrôles de contenu sont enregistrées dans la partie XML personnalisée.

 Cette procédure pas à pas décrit les tâches suivantes :

- Ajout de contrôles de contenu au document Word d'un projet de niveau document au moment du design.

- Création d'un fichier de données XML et d'un schéma XML qui définit les éléments à lier aux contrôles de contenu.

- Liaison du schéma XML au document au moment du design.

- Ajout du contenu du fichier XML à une partie XML personnalisée dans le document lors de l’exécution.

- Liaison des contrôles de contenu aux éléments de la partie XML personnalisée.

- Liaison d’un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> à un ensemble de valeurs définies dans le schéma XML.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-document-project"></a>Créez un projet de document Word
 Créez un document Word que vous utiliserez dans la procédure pas à pas.

### <a name="to-create-a-new-word-document-project"></a>Pour créer un projet de document Word

1. Créer un projet de document Word portant le nom **EmployeeControls**. Créez un document pour la solution. Pour plus d'informations, voir [Procédure : Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ouvre le nouveau document Word dans le concepteur et ajoute le **EmployeeControls** projet **l’Explorateur de solutions**.

## <a name="add-content-controls-to-the-document"></a>Ajouter des contrôles de contenu au document
 Créez une table qui contient trois types différents de contrôles de contenu, où l'utilisateur peut afficher ou modifier les informations sur un employé.

### <a name="to-add-content-controls-to-the-document"></a>Pour ajouter des contrôles de contenu au document

1. Dans le document Word qui est hébergé dans le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer, dans le ruban, choisissez le **insérer** onglet.

2. Dans le **Tables** de groupe, choisissez **Table**et insérez un tableau comportant 2 colonnes et 3 lignes.

3. Tapez un texte dans la première colonne afin qu'elle se présente de la façon suivante :

   ||
   |-|
   |**Nom de l’employé**|
   |**Date d’embauche**|
   |**Titre**|

4. Dans la deuxième colonne de la table, choisissez la première ligne (regard **nom de l’employé**).

5. Dans le ruban, choisissez le **développeur** onglet.

   > [!NOTE]
   > Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d'informations, voir [Procédure : Afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. Dans le **contrôles** de groupe, choisissez le **texte** bouton ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") pour ajouter un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>à la première cellule.

7. Dans la deuxième colonne de la table, choisissez la deuxième ligne (regard **Date d’embauche**).

8. Dans le **contrôles** de groupe, choisissez le **sélecteur de dates** bouton ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") pour ajouter un <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> dans la deuxième cellule.

9. Dans la deuxième colonne de la table, sélectionnez la troisième ligne (regard **titre**).

10. Dans le **contrôles** de groupe, choisissez le **liste déroulante** bouton ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") à ajouter un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> jusqu'à la dernière cellule.

    Il s'agit de la totalité de l'interface utilisateur pour ce projet. Si vous exécutez le projet maintenant, vous pouvez entrer un texte dans la première ligne et sélectionner une date dans la deuxième ligne. L'étape suivante consiste à lier les données que vous souhaitez afficher au document d'un fichier XML.

## <a name="create-the-xml-data-file"></a>Créer le fichier de données XML
 En règle générale, vous obtiendrez les données XML à stocker dans une partie XML personnalisée à partir d'une source externe, telle qu'un fichier ou une base de données. Dans cette procédure pas à pas, vous créez un fichier XML qui contient les données d'employé, accompagnées des éléments que vous souhaitez lier aux contrôles de contenu du document. Pour rendre les données disponibles lors de l'exécution, incorporez le fichier XML en tant que ressource dans l'assembly de personnalisation.

#### <a name="to-create-the-data-file"></a>Pour créer le fichier de données

1. Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s’affiche.

2. Dans le **modèles** volet, sélectionnez **fichier XML**.

3. Nommez le fichier **employees.xml**, puis choisissez le **ajouter** bouton.

     Le **employees.xml** fichier s’ouvre dans l’éditeur de Code.

4. Remplacez le contenu de la **employees.xml** fichier avec le texte suivant.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">
      <employee>
        <name>Karina Leal</name>
        <hireDate>1999-04-01</hireDate>
        <title>Manager</title>
      </employee>
    </employees>
    ```

5. Dans **l’Explorateur de solutions**, choisissez le **employees.xml** fichier.

6. Dans le **propriétés** fenêtre, sélectionnez le **Action de génération** propriété, puis modifiez la valeur à **ressource incorporée**.

     Cette étape incorpore le fichier XML en tant que ressource dans l'assembly lorsque vous générez le projet. Cela vous permet d’accéder au contenu du fichier XML lors de l’exécution.

## <a name="create-an-xml-schema"></a>Créer un schéma XML
 Si vous souhaitez lier un contrôle de contenu à un seul élément unique d'une partie XML personnalisée, vous n'avez pas à utiliser de schéma XML. Toutefois, pour lier le <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> à un ensemble de valeurs, vous devez créer un schéma XML qui valide le fichier de données XML que vous avez créé précédemment. Le schéma XML définit les valeurs possibles pour l'élément `title`. Vous allez lier le <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> à cet élément plus loin dans cette procédure pas à pas.

#### <a name="to-create-an-xml-schema"></a>Pour créer un schéma XML

1. Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s’affiche.

2. Dans le **modèles** volet, sélectionnez **schéma XML**.

3. Nommez le schéma **employees.xsd** et choisissez le **ajouter** bouton.

     Le Concepteur de schémas s'ouvre.

4. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **employees.xsd**, puis choisissez **afficher le Code**.

5. Remplacez le contenu de la **employees.xsd** fichier avec le schéma suivant.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"
        targetNamespace="http://schemas.microsoft.com/vsto/samples"
        xmlns:xs="http://www.w3.org/2001/XMLSchema"
        elementFormDefault="qualified">
      <xs:element name="employees" type="EmployeesType"></xs:element>
      <xs:complexType name="EmployeesType">
        <xs:all>
          <xs:element name="employee" type="EmployeeType"/>
        </xs:all>
      </xs:complexType>
      <xs:complexType name="EmployeeType">
        <xs:sequence>
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>
        </xs:sequence>
      </xs:complexType>
      <xs:simpleType name="TitleType">
        <xs:restriction base="xs:string">
          <xs:enumeration value ="Engineer"/>
          <xs:enumeration value ="Designer"/>
          <xs:enumeration value ="Manager"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:schema>
    ```

6. Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer vos modifications dans le **employees.xml** et **employees.xsd** fichiers.

## <a name="attach-the-xml-schema-to-the-document"></a>Attacher le schéma XML au document
 Vous devez joindre le schéma XML au document afin de lier le <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> aux valeurs valides de l'élément `title`.

### <a name="to-attach-the-xml-schema-to-the-document--includeword15shortvstoincludesword-15-short-mdmd"></a>Pour attacher le schéma XML au document ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)])

1. Activer **EmployeeControls.docx** dans le concepteur.

2. Dans le ruban, choisissez le **développeur** onglet, puis choisissez le **Add-Ins** bouton.

3. Dans le **modèles et compléments** boîte de dialogue, sélectionnez le **schéma XML** onglet, puis choisissez le **ajouter un schéma** bouton.

4. Accédez à la **employees.xsd** schéma créé précédemment, ce qui se trouve dans votre répertoire de projet, puis choisissez le **Open** bouton.

5. Choisissez le **OK** situé dans le **les paramètres de schéma** boîte de dialogue.

6. Choisissez le **OK** bouton pour fermer la **modèles et compléments** boîte de dialogue.

### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>Pour attacher le schéma XML au document (Word 2010)

1. Activer **EmployeeControls.docx** dans le concepteur.

2. Dans le ruban, choisissez le **développeur** onglet.

3. Dans le **XML** de groupe, choisissez le **schéma** bouton.

4. Dans le **modèles et compléments** boîte de dialogue, sélectionnez le **schéma XML** onglet, puis choisissez le **ajouter un schéma** bouton.

5. Accédez à la **employees.xsd** schéma que vous avez créé précédemment, ce qui se trouve dans votre répertoire de projet, puis choisissez le **Open** bouton.

6. Choisissez le **OK** situé dans le **les paramètres de schéma** boîte de dialogue.

7. Choisissez le **OK** bouton pour fermer la **modèles et compléments** boîte de dialogue.

     Le **Structure XML** s’ouvre le volet de tâches.

8. Fermer le **Structure XML** volet de tâches.

## <a name="add-a-custom-xml-part-to-the-document"></a>Ajouter une partie XML personnalisée au document
 Avant de pouvoir lier les contrôles de contenu aux éléments du fichier XML, vous devez ajouter le contenu du fichier XML à une nouvelle partie XML personnalisée du document.

### <a name="to-add-a-custom-xml-part-to-the-document"></a>Pour ajouter une partie XML personnalisée au document

1. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **ThisDocument.cs** ou **ThisDocument.vb**, puis choisissez **afficher le Code**.

2. Ajoutez les déclarations suivantes à la classe `ThisDocument`. Le code déclare plusieurs objets que vous utiliserez pour ajouter une partie XML personnalisée au document.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]

3. Ajoutez la méthode suivante à la classe `ThisDocument` . Cette méthode obtient le contenu du fichier de données XML qui est incorporé en tant que ressource dans l'assembly, et retourne le contenu sous la forme d'une chaîne XML.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]

4. Ajoutez la méthode suivante à la classe `ThisDocument` . La méthode `AddCustomXmlPart` crée une nouvelle partie XML personnalisée qui contient une chaîne XML qui est passée à la méthode.

     Pour vous assurer que la partie XML personnalisée n'est créée qu'une seule fois, la méthode crée cette partie uniquement si une partie XML personnalisée avec un GUID correspondant n'existe pas dans le document. La première fois que cette méthode est appelée, elle enregistre la valeur de la propriété <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> dans la chaîne `employeeXMLPartID`. La valeur de la chaîne `employeeXMLPartID` est rendue persistante dans le document, car elle a été déclarée à l'aide de l'attribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]

## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Lier les contrôles de contenu aux éléments dans la partie XML personnalisée
 Liez chaque contrôle de contenu à un élément dans la partie XML personnalisée à l’aide de la **XMLMapping** propriété de chaque contrôle de contenu.

### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Pour lier les contrôles de contenu aux éléments de la partie XML personnalisée

1. Ajoutez la méthode suivante à la classe `ThisDocument` . Cette méthode lie chaque contrôle de contenu à un élément de la partie XML personnalisée et définit le format d'affichage de date de la <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]

## <a name="run-your-code-when-the-document-is-opened"></a>Exécuter votre code lorsque le document est ouvert.
 Créez la partie XML personnalisée et liez les contrôles personnalisés aux données lorsque le document est ouvert.

### <a name="to-run-your-code-when-the-document-is-opened"></a>Pour exécuter votre code lorsque le document est ouvert

1. Ajoutez le code suivant à la méthode `ThisDocument_Startup` de la classe `ThisDocument`. Ce code obtient la chaîne XML à partir de la **employees.xml** fichier, ajoute la chaîne XML à une nouvelle partie XML personnalisée dans le document et lie les contrôles de contenu aux éléments dans la partie XML personnalisée.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]

## <a name="test-the-project"></a>Le projet de test
 Lorsque vous ouvrez le document, les contrôles de contenu affichent les données à partir des éléments de la partie XML personnalisée. Vous pouvez cliquer sur le <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> pour sélectionner l’une des trois valeurs valides pour le `title` élément, qui sont définies dans le **employees.xsd** fichier. Si vous modifiez les données dans l'un des contrôles de contenu, les nouvelles valeurs sont enregistrées dans la partie XML personnalisée du document.

### <a name="to-test-the-content-controls"></a>Pour tester les contrôles de contenu

1. Appuyez sur **F5** pour exécuter le projet.

2. Vérifiez que la table du document ressemble au tableau suivant. Chacune des chaînes de la deuxième colonne est obtenue à partir d'un élément de la partie XML personnalisée du document.

    |||
    |-|-|
    |**Nom de l’employé**|**Karina Leal**|
    |**Date d’embauche**|**1er avril 1999.**|
    |**Titre**|**Manager**|

3. Cliquez sur la cellule à droite de la **nom de l’employé** de la cellule et tapez un nom différent.

4. Cliquez sur la cellule à droite de la **Date d’embauche** de la cellule et sélectionnez une autre date dans le sélecteur de date.

5. Cliquez sur la cellule à droite de la **titre** de la cellule et sélectionnez un nouvel élément dans la liste déroulante.

6. Enregistrez le document et fermez-le.

7. Dans l’Explorateur de fichiers, ouvrez le *\bin\Debug* dossier sous l’emplacement de votre projet.

8. Ouvrez le menu contextuel pour **EmployeeControls.docx** , puis **renommer**.

9. Nommez le fichier **EmployeeControls.docx.zip**.

     Le **EmployeeControls.docx** document est enregistré au Format Open XML. En renommant ce document avec la *.zip* fichier l’extension de nom, vous pouvez examiner le contenu du document. Pour plus d’informations sur Open XML, consultez l’article technique [présentation d’Office (2007) Open XML formats de fichier](/previous-versions/office/developer/office-2007/aa338205(v=office.12)).

10. Ouvrez le **EmployeeControls.docx.zip** fichier.

11. Ouvrez le **customXml** dossier.

12. Ouvrez le menu contextuel pour **item2.xml** , puis **Open**.

     Ce fichier contient la partie XML personnalisée que vous avez ajoutée au document.

13. Vérifiez que les éléments `name`, `hireDate` et `title` contiennent les nouvelles valeurs que vous avez entrées dans les contrôles de contenu du document.

14. Fermer le **item2.xml** fichier.

## <a name="next-steps"></a>Étapes suivantes
 Pour plus d'informations sur l'utilisation des contrôles de contenu, consultez les rubriques suivantes :

- Utilisez tous les contrôles de contenu disponibles pour créer un modèle. Pour plus d’informations, consultez [Procédure pas à pas : Créer un modèle à l’aide de contrôles de contenu](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).

- Modifiez les données des parties XML personnalisées lorsque le document est fermé. La prochaine fois que l'utilisateur ouvre le document, les contrôles de contenu liés aux éléments XML affichent les nouvelles données.

- Utilisez les contrôles de contenu pour protéger les parties d'un document. Pour plus d'informations, voir [Procédure : Protéger des parties de documents à l’aide de contrôles de contenu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="see-also"></a>Voir aussi
- [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)
- [Contrôles de contenu](../vsto/content-controls.md)
- [Guide pratique pour Ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Guide pratique pour Protéger des parties de documents à l’aide de contrôles de contenu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
