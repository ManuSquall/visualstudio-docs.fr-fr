---
title: "Proc&#233;dure pas &#224; pas&#160;: liaison de contr&#244;les de contenu &#224; des parties XML personnalis&#233;es"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "contrôles de contenu (développement Office dans Visual Studio), liaison de données"
  - "parties XML personnalisées, lier à des contrôles de contenu"
  - "liaison de données (développement Office dans Visual Studio), contrôles de contenu"
  - "DatePickerContentControl, lier à une partie XML personnalisée"
  - "DropDownListContentControl, lier des éléments à une partie XML personnalisée"
  - "PlainTextContentControl, lier à une partie XML personnalisée"
ms.assetid: 10d67769-6157-4703-a10c-d33e988f9095
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Proc&#233;dure pas &#224; pas&#160;: liaison de contr&#244;les de contenu &#224; des parties XML personnalis&#233;es
  Cette procédure pas à pas montre comment lier les contrôles de contenu d'une personnalisation au niveau du document pour Word aux données XML stockées dans le document.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word permet de stocker les données XML, nommées  *parties XML personnalisées*, dans un document.  Vous pouvez contrôler l'affichage de ces données en liant les contrôles de contenu aux éléments d'une partie XML personnalisée.  L'exemple de document de cette procédure pas à pas affiche les informations sur les employés qui sont stockées dans une partie XML personnalisée.  Lorsque vous ouvrez le document, les contrôles de contenu affichent les valeurs des éléments XML.  Les modifications que vous apportez au texte des contrôles de contenu sont enregistrées dans la partie XML personnalisée.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout de contrôles de contenu au document Word d'un projet de niveau document au moment du design.  
  
-   Création d'un fichier de données XML et d'un schéma XML qui définit les éléments à lier aux contrôles de contenu.  
  
-   Liaison du schéma XML au document au moment du design.  
  
-   Ajout du contenu du fichier XML à une partie XML personnalisée du document au moment de l'exécution.  
  
-   Liaison des contrôles de contenu aux éléments de la partie XML personnalisée.  
  
-   Liaison d'un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> à un ensemble de valeurs définies dans le schéma XML.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## Création d'un projet de document Word  
 Créez un document Word que vous utiliserez dans la procédure pas à pas.  
  
#### Pour créer un projet de document Word  
  
1.  Créez un projet de document Word et nommez\-le EmployeeControls.  Créez un document pour la solution.  Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le nouveau document Word dans le concepteur et ajoute le projet EmployeeControls à l'**Explorateur de solutions**.  
  
## Ajout de contrôles de contenu au document  
 Créez une table qui contient trois types différents de contrôles de contenu, où l'utilisateur peut afficher ou modifier les informations sur un employé.  
  
#### Pour ajouter des contrôles de contenu au document  
  
1.  Dans le document Word qui est hébergé dans le concepteur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sur le ruban, cliquez sur l'onglet **Insertion**.  
  
2.  Dans le groupe **Tables**, choisissez **Table** et insérez un tableau comportant 2 colonnes et 3 lignes.  
  
3.  Tapez un texte dans la première colonne afin qu'elle se présente de la façon suivante :  
  
    ||  
    |-|  
    |Nom de l'employé|  
    |Date d'embauche|  
    |Titre|  
  
4.  Dans la deuxième colonne de la table, sélectionnez la première ligne \(en regard de **Nom de l'employé**\).  
  
5.  Dans le ruban, cliquez sur l'onglet **Développeur**.  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez d'abord l'afficher.  Pour plus d'informations, consultez [Comment : afficher l'onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  Dans le groupe **Contrôles**, cliquez sur le bouton **Texte** ![PlainTextContentControl](~/vsto/media/plaintextcontrol.gif "PlainTextContentControl") pour ajouter un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> à la première cellule.  
  
7.  Dans la deuxième colonne de la table, sélectionnez la deuxième ligne \(en regard de **Date d'embauche**\).  
  
8.  Dans le groupe **Contrôles**, cliquez sur le bouton **Sélecteur de dates** ![DatePickerContentControl](~/vsto/media/datepicker.gif "DatePickerContentControl") pour ajouter un <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> à la deuxième cellule.  
  
9. Dans la deuxième colonne de la table, sélectionnez la troisième ligne \(en regard de **Titre**\).  
  
10. Dans le groupe **Contrôles**, cliquez sur le bouton **Liste déroulante** ![DropDownListContentControl](~/vsto/media/dropdownlist.gif "DropDownListContentControl") pour ajouter un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> à la dernière cellule.  
  
 Il s'agit de la totalité de l'interface utilisateur pour ce projet.  Si vous exécutez le projet maintenant, vous pouvez entrer un texte dans la première ligne et sélectionner une date dans la deuxième ligne.  L'étape suivante consiste à lier les données que vous souhaitez afficher au document d'un fichier XML.  
  
## Création du fichier de données XML  
 En règle générale, vous obtiendrez les données XML à stocker dans une partie XML personnalisée à partir d'une source externe, telle qu'un fichier ou une base de données.  Dans cette procédure pas à pas, vous créez un fichier XML qui contient les données d'employé, accompagnées des éléments que vous souhaitez lier aux contrôles de contenu du document.  Pour rendre les données disponibles lors de l'exécution, incorporez le fichier XML en tant que ressource dans l'assembly de personnalisation.  
  
#### Pour créer le fichier de données  
  
1.  Dans le menu **Projet**, choisissez **Ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s'affiche alors.  
  
2.  Dans le volet **Modèles**, sélectionnez **Fichier XML**.  
  
3.  Nommez le fichier **employees.xml**, puis choisissez le bouton **Ajouter**.  
  
     Le fichier **employees.xml** s'ouvre dans l'éditeur de code.  
  
4.  Remplacez le contenu du fichier **employees.xml** par le texte suivant.  
  
    ```  
  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
      <employee>  
        <name>Karina Leal</name>  
        <hireDate>1999-04-01</hireDate>  
        <title>Manager</title>  
      </employee>  
    </employees>  
    ```  
  
5.  Dans l'**Explorateur de solutions**, choisissez le fichier **employees.xml**.  
  
6.  Dans la fenêtre **Propriétés**, sélectionnez la propriété **Action de génération**, puis remplacez la valeur par **Ressource incorporée**.  
  
     Cette étape incorpore le fichier XML en tant que ressource dans l'assembly lorsque vous générez le projet.  Vous pouvez ainsi accéder au contenu du fichier XML au moment de l'exécution.  
  
## Création d'un schéma XML  
 Si vous souhaitez lier un contrôle de contenu à un seul élément unique d'une partie XML personnalisée, vous n'avez pas à utiliser de schéma XML.  Toutefois, pour lier le <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> à un ensemble de valeurs, vous devez créer un schéma XML qui valide le fichier de données XML que vous avez créé précédemment.  Le schéma XML définit les valeurs possibles pour l'élément `title`.  Vous allez lier le <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> à cet élément plus loin dans cette procédure pas à pas.  
  
#### Pour créer un schéma XML  
  
1.  Dans le menu **Projet**, choisissez **Ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s'affiche alors.  
  
2.  Dans le volet **Modèles**, sélectionnez **Schéma XML**.  
  
3.  Nommez le schéma **employés.xsd** et choisissez le bouton **Ajouter**.  
  
     Le Concepteur de schémas s'ouvre.  
  
4.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel pour **employees.xsd**, puis choisissez **Afficher le code**.  
  
5.  Remplacez le contenu du fichier **employees.xml** par le schéma suivant.  
  
    ```  
  
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
  
6.  Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer les modifications apportées aux fichiers **employees.xml** et **employees.xsd**.  
  
## Liaison du schéma XML au document  
 Vous devez joindre le schéma XML au document afin de lier le <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> aux valeurs valides de l'élément `title`.  
  
#### Pour attacher le schéma XML au document \([!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]\)  
  
1.  Activez **EmployeeControls.docx** dans le concepteur.  
  
2.  Sur le Ruban, cliquez sur l'onglet **Développeur**, puis choisissez le bouton **Compléments**.  
  
3.  Dans la boîte de dialogue **Modèles et compléments**, choisissez l'onglet **Schéma XML**, puis choisissez le bouton **Ajouter un schéma**.  
  
4.  Accédez au schéma **employees.xsd** que vous avez créé précédemment, et qui se trouve dans votre répertoire de projet, puis choisissez le bouton **Ouvrir**.  
  
5.  Choisissez le bouton **OK** de la boîte de dialogue **Paramètres de schéma**.  
  
6.  Choisissez le bouton **OK** pour fermer la boîte de dialogue **Modèles et compléments**.  
  
#### Pour attacher le schéma XML au document \(Word 2010\)  
  
1.  Activez **EmployeeControls.docx** dans le concepteur.  
  
2.  Dans le ruban, cliquez sur l'onglet **Développeur**.  
  
3.  Dans le groupe **XML**, choisissez le bouton **Schéma**.  
  
4.  Dans la boîte de dialogue **Modèles et compléments**, choisissez l'onglet **Schéma XML**, puis choisissez le bouton **Ajouter un schéma**.  
  
5.  Accédez au schéma **employees.xsd** que vous avez créé précédemment, et qui se trouve dans votre répertoire de projet, puis choisissez le bouton **Ouvrir**.  
  
6.  Choisissez le bouton **OK** de la boîte de dialogue **Paramètres de schéma**.  
  
7.  Choisissez le bouton **OK** pour fermer la boîte de dialogue **Modèles et compléments**.  
  
     Le volet de tâches **Structure XML** s'ouvre.  
  
8.  Fermez le volet de tâches **Structure XML**.  
  
## Ajout d'une partie XML personnalisée au document  
 Avant de pouvoir lier les contrôles de contenu aux éléments du fichier XML, vous devez ajouter le contenu du fichier XML à une nouvelle partie XML personnalisée du document.  
  
#### Pour ajouter une partie XML personnalisée au document  
  
1.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel de **ThisDocument.cs** ou **ThisDocument.vb**, puis choisissez **Afficher le code**.  
  
2.  Ajoutez les déclarations suivantes à la classe `ThisDocument`.  Le code déclare plusieurs objets que vous utiliserez pour ajouter une partie XML personnalisée au document.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#1)]  
  
3.  Ajoutez la méthode suivante à la classe `ThisDocument`.  Cette méthode obtient le contenu du fichier de données XML qui est incorporé en tant que ressource dans l'assembly, et retourne le contenu sous la forme d'une chaîne XML.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#3)]  
  
4.  Ajoutez la méthode suivante à la classe `ThisDocument`.  La méthode `AddCustomXmlPart` crée une nouvelle partie XML personnalisée qui contient une chaîne XML qui est passée à la méthode.  
  
     Pour vous assurer que la partie XML personnalisée n'est créée qu'une seule fois, la méthode crée cette partie uniquement si une partie XML personnalisée avec un GUID correspondant n'existe pas dans le document.  La première fois que cette méthode est appelée, elle enregistre la valeur de la propriété <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> dans la chaîne `employeeXMLPartID`.  La valeur de la chaîne `employeeXMLPartID` est rendue persistante dans le document, car elle a été déclarée à l'aide de l'attribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#4)]  
  
## Liaison des contrôles de contenu aux éléments de la partie XML personnalisée  
 Liez chaque contrôle de contenu à un élément de la partie XML personnalisée à l'aide de la propriété **XMLMapping** de chaque contrôle de contenu.  
  
#### Pour lier les contrôles de contenu aux éléments de la partie XML personnalisée  
  
1.  Ajoutez la méthode suivante à la classe `ThisDocument`.  Cette méthode lie chaque contrôle de contenu à un élément de la partie XML personnalisée et définit le format d'affichage de date de la <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#5)]  
  
## Exécution de votre code lorsque le document est ouvert  
 Créez la partie XML personnalisée et liez les contrôles personnalisés aux données lorsque le document est ouvert.  
  
#### Pour exécuter votre code lorsque le document est ouvert  
  
1.  Ajoutez le code suivant à la méthode `ThisDocument_Startup` de la classe `ThisDocument`.  Ce code obtient la chaîne XML à partir du fichier **employees.xml**, ajoute la chaîne XML à une nouvelle partie XML personnalisée du document et lie les contrôles de contenu aux éléments de la partie XML personnalisée.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#2)]  
  
## Test du projet  
 Lorsque vous ouvrez le document, les contrôles de contenu affichent les données à partir des éléments de la partie XML personnalisée.  Vous pouvez cliquer sur le <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> pour sélectionner l'une des trois valeurs valides de l'élément `title`, qui sont définies dans le fichier **employees.xsd**.  Si vous modifiez les données dans l'un des contrôles de contenu, les nouvelles valeurs sont enregistrées dans la partie XML personnalisée du document.  
  
#### Pour tester les contrôles de contenu  
  
1.  Appuyez sur F5 pour exécuter le projet.  
  
2.  Vérifiez que la table du document ressemble au tableau suivant.  Chacune des chaînes de la deuxième colonne est obtenue à partir d'un élément de la partie XML personnalisée du document.  
  
    |||  
    |-|-|  
    |Nom de l'employé|**Karina Leal**|  
    |Date d'embauche|**1 avril 1999**|  
    |Titre|**Responsable**|  
  
3.  Cliquez sur la cellule à droite de la cellule du nom de l'employé et tapez un nom différent.  
  
4.  Cliquez sur la cellule à droite de la cellule de la date d'embauche et sélectionnez une autre date dans le sélecteur de dates.  
  
5.  Cliquez sur la cellule à droite de la cellule de titre et sélectionnez un nouvel élément dans la liste déroulante.  
  
6.  Enregistrez le document et fermez\-le.  
  
7.  Dans l'Explorateur de fichiers, ouvrez le dossier \\bin\\Debug sous l'emplacement de votre projet.  
  
8.  Ouvrez le menu contextuel pour EmployeeControls.docx, puis choisissez **Renommer**.  
  
9. Nommez le fichier EmployeeControls.docx.zip.  
  
     Le document EmployeeControls.docx est enregistré au format Open XML.  En renommant ce document avec l'extension de nom de fichier .zip, vous pouvez examiner le contenu du document.  Pour plus d'informations sur Open XML, consultez l'article technique [Présentation des formats de fichier Office \(2007\) Open XML\)](http://msdn.microsoft.com/fr-fr/96018532-f62c-4da7-bbff-16b96a483fbf).  
  
10. Ouvrez le fichier EmployeeControls.docx.zip.  
  
11. Ouvrez le dossier **customXml**.  
  
12. Ouvrez le menu contextuel pour **item2.xml**, puis choisissez **Ouvrir**.  
  
     Ce fichier contient la partie XML personnalisée que vous avez ajoutée au document.  
  
13. Vérifiez que les éléments `name`, `hireDate` et `title` contiennent les nouvelles valeurs que vous avez entrées dans les contrôles de contenu du document.  
  
14. Fermez le fichier **item2.xml**.  
  
## Étapes suivantes  
 Pour plus d'informations sur l'utilisation des contrôles de contenu, consultez les rubriques suivantes :  
  
-   Utilisez tous les contrôles de contenu disponibles pour créer un modèle.  Pour plus d'informations, consultez [Procédure pas à pas : création d'un modèle à l'aide de contrôles de contenu](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
-   Modifiez les données des parties XML personnalisées lorsque le document est fermé.  La prochaine fois que l'utilisateur ouvre le document, les contrôles de contenu liés aux éléments XML affichent les nouvelles données.  
  
-   Utilisez les contrôles de contenu pour protéger les parties d'un document.  Pour plus d'informations, consultez [Comment : protéger des parties de documents à l'aide de contrôles de contenu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## Voir aussi  
 [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Contrôles de contenu](../vsto/content-controls.md)   
 [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Comment : protéger des parties de documents à l'aide de contrôles de contenu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  