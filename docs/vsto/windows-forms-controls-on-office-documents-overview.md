---
title: Contrôles Windows Forms dans une vue d’ensemble des Documents Office | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- old data showing in error [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], Word
- Windows Forms controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], arranging
- data [Office development in Visual Studio], old data showing in error
- user controls [Office development in Visual Studio], Windows Forms
- Windows Forms controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], removing
- application development [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Windows Forms controls
- Office [Office development in Visual Studio], Windows Forms controls
- Office documents [Office development in Visual Studio, controls
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], about Windows Forms controls
- Office applications [Office development in Visual Studio], Windows Forms
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2693c31d06edc621f355749f76caf04e44fb28e1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="windows-forms-controls-on-office-documents-overview"></a>Vue d'ensemble des contrôles Windows Forms dans les documents Office
  Les contrôles Windows Forms sont des objets avec lesquels les utilisateurs peuvent interagir pour entrer ou manipuler des données. Dans des projets au niveau du document pour Microsoft Office Excel et Microsoft Office Word, vous pouvez ajouter des contrôles Windows Forms au document ou au classeur dans votre projet au moment du design, ou vous pouvez ajouter ces contrôles par programmation au moment de l’exécution. Vous pouvez ajouter ces contrôles par programmation à tout document ou feuille de calcul ouvert(e) au moment de l’exécution dans un complément VSTO pour Excel ou Word.  
  
 Pour plus d'informations, consultez [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="using-windows-forms-controls"></a>Utilisation des contrôles Windows Forms  
 Vous pouvez ajouter des contrôles Windows Forms à des documents et à des éléments d’interface utilisateur personnalisables, y compris des volets d’actions, des volets Office personnalisés et des Windows Forms. Les contrôles Windows Forms ont généralement le même comportement dans des documents que sur ces autres éléments d’interface utilisateur, mais il existe certaines différences. Pour plus d'informations, consultez [Limitations des contrôles Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
 La décision d’ajouter des contrôles Windows Forms à un document ou à un autre élément d’interface utilisateur dépend de plusieurs facteurs. Lors de la conception de l’interface utilisateur de votre solution, vous pouvez utiliser les contrôles Windows Forms comme décrit dans le tableau suivant.  
  
 Dans un document.  
 -   Lorsque vous souhaitez afficher les contrôles en permanence.  
  
-   Lorsque vous souhaitez que les utilisateurs entrent des données directement dans le document, par exemple dans des documents basés sur des formulaires où la surface d’édition est verrouillée.  
  
-   Lorsque vous souhaitez que les contrôles soient alignés avec les données dans le document. Par exemple, si vous ajoutez des boutons à chaque ligne d’un objet de liste, il vaut mieux qu’ils soient alignés avec chaque élément de liste.  
  
 Dans le volet d’actions ou un volet Office personnalisé.  
 -   Lorsque vous souhaitez fournir des informations contextuelles à l’utilisateur.  
  
-   Lorsque vous souhaitez que seuls les résultats, et non les contrôles de requête et les données, apparaissent dans le document.  
  
-   Lorsque vous souhaitez vous assurer que les contrôles ne soient pas imprimés avec le document.  
  
-   Lorsque vous souhaitez vous assurer que les contrôles n’interfèrent pas avec la vue du document.  
  
 Dans un Windows Form.  
 -   Lorsque vous souhaitez contrôler la taille de l’interface utilisateur.  
  
-   Lorsque vous souhaitez empêcher les utilisateurs de masquer ou de supprimer les contrôles.  
  
-   Lorsque vous souhaitez obtenir des informations à partir de l’utilisateur et l’empêcher de faire quoi que ce soit dans le document avant que ces informations aient été reçues.  
  
## <a name="adding-windows-forms-controls-programmatically"></a>Ajout de contrôles Windows Forms par programmation  
 Vous pouvez ajouter des contrôles Windows Forms à des documents Word et des feuilles de calcul Excel au moment de l’exécution. Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] fournit des méthodes d’assistance pour ajouter les contrôles Windows Forms les plus courants. Ces méthodes d’assistance vous permettent d’ajouter rapidement des contrôles à votre document Office et d’accéder à la fonctionnalité Windows Forms et Office combinée de ces contrôles.  
  
 Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="using-windows-forms-controls-in-document-level-projects"></a>Utilisation de contrôles Windows Forms dans des projets au niveau du document  
 Certains aspects liés à l’utilisation des contrôles Windows Forms sur les documents sont uniques aux projets au niveau du document, qui vous permettent de concevoir l’interface utilisateur de votre document en utilisant le concepteur Visual Studio.  
  
### <a name="creating-custom-user-controls"></a>Création de contrôles utilisateur personnalisés  
 Vous pouvez ajouter un contrôle utilisateur à votre projet, puis l’ajouter à la **Boîte à outils**. Vous pouvez ensuite faire glisser le contrôle utilisateur directement sur votre document, comme vous le feriez pour y ajouter un contrôle Windows Forms. Notez les points suivants lors de la création de contrôles utilisateur :  
  
-   Ne créez pas un contrôle utilisateur **sealed** . Lorsque vous faites glisser le contrôle sur votre document, Visual Studio génère une classe wrapper dérivée du contrôle utilisateur pour l’étendre et prendre en charge son utilisation dans le document. Si le contrôle utilisateur est **sealed**, Visual Studio ne peut pas générer la classe wrapper.  
  
-   L’attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> des contrôles utilisateur doit avoir la valeur **true**. Contrôles utilisateur créés à l’intérieur d’un projet Office ont cet attribut la valeur **true** par défaut, mais les utilisateurs des contrôles qui font partie de projets extérieurs peut-être pas cet attribut la valeur **true**.  
  
-   Après avoir ajouté un contrôle utilisateur au document, ne renommez pas et supprimez pas la classe <xref:System.Windows.Forms.UserControl> du projet. Si vous devez modifier le nom d’un contrôle utilisateur, vous devez tout d’abord le supprimer du document, puis le rajouter après avoir modifié le nom.  
  
### <a name="arranging-controls-at-design-time"></a>Réorganisation des contrôles au moment du design  
 Si vous ajoutez plusieurs contrôles à vos documents Word et Excel au moment du design, vous pouvez rapidement définir l’alignement de tous les contrôles sélectionnés à l’aide des barres d’outils **Microsoft Office Word** et **Microsoft Office Excel** dans Visual Studio. Ces barres d’outils sont disponibles uniquement quand un document ou une feuille de calcul est ouvert(e) dans le concepteur.  
  
 Quand vous sélectionnez plusieurs contrôles dans le concepteur, vous pouvez utiliser les boutons suivants sur ces barres d’outils pour réorganiser les contrôles :  
  
-   **Aligner les côtés gauches**  
  
-   **Aligner les centres**  
  
-   **Aligner les côtés droits**  
  
-   **Aligner les sommets**  
  
-   **Aligner les milieux**  
  
-   **Aligner les bases**  
  
-   **Égaliser l'espacement horizontal**  
  
-   **Égaliser l'espacement vertical**  
  
> [!NOTE]  
>  Dans les projets Word, ces boutons sont activés uniquement si les contrôles sélectionnés ne sont pas alignés avec le texte. Par défaut, les contrôles que vous ajoutez au document au moment du design sont alignés avec le texte.  
  
### <a name="preventing-old-data-from-appearing-in-excel-workbooks-during-loading"></a>Empêcher des données anciennes d’apparaître dans les classeurs Excel pendant le chargement  
 Lorsque vous ajoutez des contrôles Windows Forms à des documents ou des feuilles de calcul au moment du design, les contrôles restent dans le document quand l’utilisateur le ferme. Les contrôles ajoutés au moment du design sont également appelés *contrôles statiques*.  
  
 Quand vous ouvrez un classeur Excel qui contient des contrôles statiques, il affiche une bitmap du contrôle dans un contrôle ActiveX jusqu’à ce que le code de personnalisation s’exécute et charge le contrôle proprement dit. Excel crée cette bitmap et la stocke dans le classeur chaque fois que celui-ci est enregistré. La bitmap affiche le contrôle tel qu’il apparaissait la dernière fois que le classeur a été enregistré, y compris les données affichées par le contrôle. Pour plus d’informations sur le contrôle ActiveX qui contient des contrôles Windows Forms et des bitmaps, consultez [Limitations des contrôles Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
 Dans certaines conditions, par exemple lorsque l’utilisateur ouvre le classeur en mode Création, le code n’est pas chargé et seule la bitmap est affichée. En outre, si l’utilisateur ouvre le classeur sur un ordinateur sur lequel le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] n’est pas installé, la personnalisation ne peut pas s’exécuter pour charger les contrôles et seule la bitmap du contrôle est visible. Vous devez toujours supprimer les informations personnelles des contrôles dans les classeurs avant de les enregistrer et de les envoyer à un autre utilisateur, pour éviter toute divulgation involontaire.  
  
### <a name="matching-control-size-to-cell-size-on-an-excel-worksheet"></a>Mise en correspondance de la taille de contrôle et de la taille de cellule sur une feuille de calcul Excel  
 Vous pouvez configurer le contrôle pour qu’il soit redimensionné automatiquement quand la taille de la cellule parente change. Pour plus d’informations, consultez [Comment : redimensionner des contrôles dans des cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="adding-components-that-are-shared-by-all-worksheets"></a>Ajout de composants partagés par toutes les feuilles de calcul  
 Vous pouvez ajouter des composants que vous souhaitez partager parmi toutes les feuilles de calcul, comme un <xref:System.Data.DataSet>, au Concepteur de classeurs plutôt qu’aux feuilles de calcul. Le composant apparaîtra dans la barre d’état des composants.  
  
### <a name="formula-for-embedding-controls-on-an-excel-worksheet"></a>Formule pour incorporer des contrôles dans une feuille de calcul Excel  
 Quand vous sélectionnez un contrôle dans Excel, vous voyez **=EMBED("WinForms.Control.Host","")** dans la **Barre de formule**. Ce texte est nécessaire et ne doit pas être supprimé.  
  
### <a name="layout-style-of-controls-on-a-word-document"></a>Style de disposition des contrôles dans un document Word  
 Quand vous ajoutez un contrôle au document Word dans un projet au niveau du document à l’aide du concepteur Visual Studio, le contrôle est aligné avec le texte. Pour modifier le style de disposition du contrôle, cliquez avec le bouton droit sur le contrôle, puis cliquez sur **Format de contrôle**. Sélectionnez un style d’habillage dans la page **Disposition** de la boîte de dialogue **Format d’objet** .  
  
 Lorsque vous ajoutez un contrôle à un document Word au moment de l’exécution, vous pouvez spécifier le style de disposition du nouveau contrôle à l’aide de différents `Add` \< *classe contrôle*> surcharges de méthode de la <xref:Microsoft.Office.Tools.Word.ControlCollection> classe :  
  
-   Pour aligner le contrôle avec le texte, utilisez une surcharge qui accepte un <xref:Microsoft.Office.Interop.Word.Range> qui spécifie l’emplacement du contrôle.  
  
-   Pour ajouter le contrôle en tant que forme flottante, utilisez une surcharge qui accepte les coordonnées de gauche et supérieure du contrôle.  
  
 Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Si vous ouvrez un modèle Word dans le concepteur Visual Studio, les contrôles non inline sur le modèle ne seront peut-être pas visibles, car Visual Studio ouvre le modèle en mode **Normal** . Pour afficher les contrôles, basculez en mode **Page**.  
  
### <a name="controls-outside-the-main-document-body"></a>Contrôles en dehors du corps de document principal  
 Les contrôles Windows Forms ne sont pas pris en charge dans un en-tête ou un pied de page, ni dans un sous-document.  
  
### <a name="adding-components-at-design-time"></a>Ajout de composants au moment du design  
 Certains contrôles ou composants ne sont pas visibles dans le document, mais sont plutôt affichés dans une barre d’état des composants. Visual Studio fournit une barre d’état des composants pour chaque fenêtre de document. La barre d’état des composants est affichée à l’écran uniquement s’il existe des composants dans le document.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles sur des Documents Office](../vsto/controls-on-office-documents.md)   
 [Ajout de contrôles aux Documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)   
 [Contrôles Windows Forms](/dotnet/framework/winforms/controls/index)   
 [Limitations des contrôles Windows Forms sur des Documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [Comment : ajouter des contrôles Windows Forms à des Documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Comment : redimensionner des contrôles dans les cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Comment : masquer des contrôles sur des feuilles de calcul lors de l’impression](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Procédure pas à pas : Modification de mise en forme de feuille de calcul à l’aide de contrôles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Procédure pas à pas : Modification de mise en forme d’un Document à l’aide de contrôles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)   
 [Procédure pas à pas : Affichage de texte dans une zone de texte dans une feuille de calcul à l’aide d’un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Procédure pas à pas : Affichage de texte dans une zone de texte dans un Document à l’aide d’un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)   
 [Limitations des contrôles Windows Forms sur des Documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [Procédure pas à pas : Mise à jour d’un graphique dans un Document à l’aide de cases d’option](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)   
 [Procédure pas à pas : mise à jour d’un graphique dans une feuille de calcul à l’aide de cases d’option](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  