---
title: Étendre des documents Word et classeurs Excel dans des Compléments VSTO lors de l’exécution
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- GetVstoObject method
- application-level add-ins [Office development in Visual Studio], adding controls to documents
- host items [Office development in Visual Studio], creating at run time in add-ins
- application-level add-ins [Office development in Visual Studio], extending Word documents
- application-level add-ins [Office development in Visual Studio], extending Excel workbooks
- controls [Office development in Visual Studio], adding at run time
- HasVstoObject method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3dd4bd7c2b473b4bb48481fee6a991dde748eb26
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
---
# <a name="extend-word-documents-and-excel-workbooks-in-vsto-add-ins-at-runtime"></a>Étendre des documents Word et classeurs Excel dans des Compléments VSTO lors de l’exécution
  Vous pouvez utiliser un complément VSTO pour personnaliser des documents Word et des classeurs Excel comme suit :  
  
-   Ajoutez des contrôles managés à tout document ou feuille de calcul ouvert.  
  
-   Convertissez un objet de liste existant sur une feuille de calcul Excel en un <xref:Microsoft.Office.Tools.Excel.ListObject> étendu qui expose des événements et qui peut être lié aux données à l'aide du modèle de liaison de données Windows Forms.  
  
-   Accédez à des événements de niveau application qui sont exposés par Word et Excel pour des documents, des classeurs et des feuilles de calcul spécifiques.  
  
 Pour utiliser cette fonctionnalité, vous générez, au moment de l'exécution, un objet qui étend le document ou le classeur.  
  
 **S'applique à :** les informations contenues dans cette rubrique s'appliquent aux projets de complément VSTO pour les applications suivantes : Excel et Word. Pour plus d’informations, consultez [fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
## <a name="generate-extended-objects-in-vsto-add-ins"></a>Générer les objets étendus dans les Compléments VSTO  
 Les*objets étendus* sont des instances des types fournis par le runtime Visual Studio Tools pour Office qui ajoutent des fonctionnalités aux objets qui existent en mode natif dans les modèles objet Word ou Excel (appelés *objets Office natifs*). Pour générer un objet étendu pour un objet Word ou Excel, utilisez la méthode `GetVstoObject`. La première fois que vous appelez le `GetVstoObject` l’objet de méthode pour un Word ou Excel spécifié, elle retourne un nouvel objet qui étend l’objet spécifié. Chaque fois que vous appelez la méthode et que vous spécifiez le même objet Word ou Excel, elle retourne le même objet étendu.  
  
 Le nom du type de l'objet étendu est identique à celui du type de l'objet Office natif, mais le type est défini dans l'espace de noms <xref:Microsoft.Office.Tools.Excel> ou <xref:Microsoft.Office.Tools.Word>. Par exemple, si vous appelez la méthode `GetVstoObject` pour étendre un objet <xref:Microsoft.Office.Interop.Word.Document>, la méthode retourne un objet <xref:Microsoft.Office.Tools.Word.Document>.  
  
 Le `GetVstoObject` méthodes sont destinées à être utilisées principalement dans les projets de complément VSTO. Vous pouvez également les utiliser dans des projets de niveau document, mais elles se comportent différemment et ont moins d'utilisations.  
  
 Pour déterminer si un objet étendu a déjà été généré pour un objet Office natif particulier, utilisez la méthode `HasVstoObject`. Pour plus d’informations, consultez [déterminer si un objet Office a été étendu](#HasVstoObject).  
  
### <a name="generate-host-items"></a>Générer des éléments hôtes  
 Lorsque vous utilisez la `GetVstoObject` pour étendre un objet au niveau du document (autrement dit, un <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, ou <xref:Microsoft.Office.Interop.Word.Document>), l’objet retourné est appelé un *élément hôte*. Un élément hôte est un type qui peut contenir d'autres objets, y compris d'autres objets et contrôles étendus. Il ressemble au type correspondant dans l'assembly PIA (Primary Interop Assembly) Word ou Excel, mais il comporte des fonctionnalités supplémentaires. Pour plus d’informations sur les éléments hôtes, consultez [éléments hôtes et héberger la vue d’ensemble des contrôles](../vsto/host-items-and-host-controls-overview.md).  
  
 Après avoir généré un élément hôte, vous pouvez l'utiliser pour ajouter des contrôles managés au document, au classeur ou à la feuille de calcul. Pour plus d’informations, consultez [Ajout de contrôles aux documents et feuilles de calcul managés](#AddControls).  
  
#### <a name="to-generate-a-host-item-for-a-word-document"></a>Pour générer un élément hôte pour un document Word  
  
-   L'exemple de code suivant montre comment générer un élément hôte pour le document actif.  
  
     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]
     [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]  
  
#### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Pour générer un élément hôte pour un classeur Excel  
  
-   L'exemple de code suivant montre comment générer un élément hôte pour le classeur actif.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]  
  
#### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Pour générer un élément hôte pour une feuille de calcul Excel  
  
-   L'exemple de code suivant montre comment générer un élément hôte de la feuille de calcul active dans un projet.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]  
  
### <a name="generate-listobject-host-controls"></a>Générer des contrôles hôtes ListObject  
 Lorsque vous utilisez la méthode `GetVstoObject` pour étendre un objet <xref:Microsoft.Office.Interop.Excel.ListObject>, la méthode retourne un objet <xref:Microsoft.Office.Tools.Excel.ListObject>. L'objet <xref:Microsoft.Office.Tools.Excel.ListObject> possède toutes les fonctionnalités de l'objet <xref:Microsoft.Office.Interop.Excel.ListObject>d'origine, mais il comporte également des fonctionnalités supplémentaires, telles que la capacité d'être lié aux données à l'aide du modèle de liaison de données Windows Forms. Pour plus d’informations, consultez [contrôle ListObject](../vsto/listobject-control.md).  
  
#### <a name="to-generate-a-host-control-for-a-listobject"></a>Pour générer un contrôle hôte pour un ListObject  
  
-   L'exemple de code suivant montre comment générer un <xref:Microsoft.Office.Tools.Excel.ListObject> pour le premier <xref:Microsoft.Office.Interop.Excel.ListObject> dans la feuille de calcul active dans un projet.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]  
  
###  <a name="AddControls"></a> Ajouter des contrôles managés aux documents et feuilles de calcul  
 Après avoir généré un objet <xref:Microsoft.Office.Tools.Word.Document> ou un objet <xref:Microsoft.Office.Tools.Excel.Worksheet>, vous pouvez ajouter des contrôles au document ou à la feuille de calcul que ces objets étendus représentent. Pour ce faire, utilisez la propriété Controls de la <xref:Microsoft.Office.Tools.Word.Document> ou <xref:Microsoft.Office.Tools.Excel.Worksheet>. Pour plus d’informations, consultez [ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Vous pouvez ajouter des contrôles Windows Forms ou des *contrôles hôtes*. Un contrôle hôte est un contrôle fourni par [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] qui encapsule un contrôle correspondant dans l'assembly PIA Word ou Excel. Un contrôle hôte expose l'ensemble du comportement de l'objet Office natif sous-jacent, mais il déclenche également des événements et peut être lié aux données à l'aide du modèle de liaison de données Windows Forms. Pour plus d’informations, consultez [éléments hôtes et héberger la vue d’ensemble des contrôles](../vsto/host-items-and-host-controls-overview.md).  
  
> [!NOTE]  
>  Vous ne pouvez pas utiliser un complément VSTO pour ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> à une feuille de calcul, ou bien un contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> ou <xref:Microsoft.Office.Tools.Word.XMLNodes> à un document. Ces contrôles ne peuvent pas être ajoutés par programmation. Pour plus d’informations, consultez [limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="persist-and-remove-controls"></a>Conserver et supprimer des contrôles  
 Lorsque vous ajoutez des contrôles managés à un document ou à une feuille de calcul, les contrôles ne sont pas persistant lorsque le document est enregistré puis fermé. Tous les contrôles hôtes sont supprimés afin que seuls les objets Office natifs sous-jacents soient conservés. Par exemple, un <xref:Microsoft.Office.Tools.Excel.ListObject> devient un <xref:Microsoft.Office.Interop.Excel.ListObject>. Tous les contrôles Windows Forms sont également supprimés, mais leurs wrappers ActiveX sont conservés dans le document. Vous devez inclure du code dans votre complément VSTO pour nettoyer les contrôles ou les recréer à l'ouverture suivante du document. Pour plus d’informations, consultez [conserver des contrôles dynamiques persistants dans des documents Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
## <a name="access-application-level-events-on-documents-and-workbooks"></a>Événements d’accès au niveau de l’application sur des documents et des classeurs  
 Certains événements de document, de classeur et de feuille de calcul dans les objets Word et Excel natifs sont déclenchés uniquement au niveau de l'application. Par exemple, l'événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> est déclenché lorsqu'un document est ouvert dans Word, mais il est défini dans la classe <xref:Microsoft.Office.Interop.Word.Application> , plutôt que dans la classe <xref:Microsoft.Office.Interop.Word.Document> .  
  
 Quand vous utilisez uniquement des objets Office natifs dans votre complément VSTO, vous devez gérer ces événements de niveau application, puis écrire du code supplémentaire afin de déterminer si le document qui a déclenché l'événement est un document que vous avez personnalisé. Les éléments hôtes fournissent ces événements au niveau du document, afin qu'il soit plus facile de les gérer pour un document spécifique. Vous pouvez générer un élément hôte, puis gérer l'événement pour cet élément hôte.  
  
### <a name="example-that-uses-native-word-objects"></a>Exemple qui utilise des objets Word natifs  
 L'exemple de code suivant montre comment gérer un événement de niveau application pour les documents Word. La méthode `CreateDocument` crée un document, puis définit un gestionnaire d'événements <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> qui empêche l'enregistrement de ce document. Étant donné qu'il s'agit d'un événement de niveau application qui est déclenché pour l'objet <xref:Microsoft.Office.Interop.Word.Application> , le gestionnaire d'événements doit comparer le paramètre `Doc` à l'objet `document1` afin de déterminer si `document1` représente le document enregistré.  
  
 [!code-vb[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)]
 [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]  
  
### <a name="examples-that-use-a-host-item"></a>Exemples d’utilisation d’un élément hôte  
 Les exemples de code suivants simplifient ce processus en gérant l'événement <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> d'un élément hôte <xref:Microsoft.Office.Tools.Word.Document> . La méthode `CreateDocument2` utilisée dans ces exemples génère un objet <xref:Microsoft.Office.Tools.Word.Document> qui étend l'objet `document2` , puis elle définit un gestionnaire d'événements <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> qui empêche l'enregistrement du document. Étant donné que ce gestionnaire d'événements est appelé uniquement lorsque `document2` est enregistré, le gestionnaire d'événements peut annuler l'action d'enregistrement sans avoir à vérifier en plus quel document a été enregistré.  
  
 L'exemple de code suivant illustre cette tâche.  
  
 [!code-vb[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)]
 [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]  
  
##  <a name="HasVstoObject"></a> Déterminer si un objet Office a été étendu.  
 Pour déterminer si un objet étendu a déjà été généré pour un objet Office natif particulier, utilisez la méthode `HasVstoObject`. Cette méthode retourne la valeur **true** un objet étendu a déjà été généré ; sinon, elle retourne la valeur **false**.  
  
 Utilisez la méthode `Globals.Factory.HasVstoMethod`. Passez l'objet Word ou Excel natif, comme un objet <xref:Microsoft.Office.Interop.Word.Document> ou <xref:Microsoft.Office.Interop.Excel.Worksheet>, pour lequel vous voulez vérifier s'il s'agit d'objet étendu.  
  
 La méthode `HasVstoObject` s'avère utile lorsque vous voulez exécuter du code uniquement lorsqu'un objet Office spécifié possède un objet étendu. Par exemple, si vous avez un complément VSTO Word qui gère l'événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> pour supprimer des contrôles managés d'un document avant qu'il soit enregistré, vous pouvez utiliser la méthode `HasVstoObject` pour déterminer si le document a été étendu. Si le document n'a pas été étendu, il ne peut pas contenir de contrôles managés, et par conséquent, le gestionnaire d'événements peut simplement retourner une valeur sans essayer de nettoyer des contrôles sur le document.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Éléments hôtes et vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Procédures pas à pas et des exemples de développement office](../vsto/office-development-samples-and-walkthroughs.md)  
  
  