---
title: "Vue d&#39;ensemble des contr&#244;les Windows Forms dans les documents Office | Microsoft Docs"
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
  - "données anciennes apparaissant comme erronées (développement Office dans Visual Studio)"
  - "contrôles Windows Forms (développement Office dans Visual Studio), Word"
  - "contrôles Windows Forms (développement Office dans Visual Studio), ajout"
  - "contrôles Windows Forms (développement Office dans Visual Studio), réorganisation"
  - "données (développement Office dans Visual Studio), données anciennes apparaissant comme erronées"
  - "contrôles utilisateur (développement Office dans Visual Studio), Windows Forms"
  - "contrôles Windows Forms (développement Office dans Visual Studio)"
  - "contrôles Windows Forms (développement Office dans Visual Studio), suppression"
  - "développement d’applications (développement Office dans Visual Studio), contrôles Windows Forms"
  - "contrôles (développement Office dans Visual Studio), contrôles Windows Forms"
  - "Office (développement Office dans Visual Studio), contrôles Windows Forms"
  - "documents Office (développement Office dans Visual Studio), contrôles"
  - "documents (développement Office dans Visual Studio), contrôles Windows Forms"
  - "personnalisations au niveau du document (développement Office dans Visual Studio), contrôles Windows Forms"
  - "contrôles Windows Forms (développement Office dans Visual Studio), à propos des contrôles Windows Forms"
  - "applications Office (développement Office dans Visual Studio), Windows Forms"
ms.assetid: a959506b-5038-49c2-831a-d63c6d6b797d
caps.latest.revision: 76
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 75
---
# Vue d&#39;ensemble des contr&#244;les Windows Forms dans les documents Office
  Les contrôles Windows Forms sont des objets avec lesquels les utilisateurs peuvent interagir pour entrer ou manipuler des données. Dans des projets au niveau du document pour Microsoft Office Excel et Microsoft Office Word, vous pouvez ajouter des contrôles Windows Forms au document ou au classeur dans votre projet au moment du design, ou vous pouvez ajouter ces contrôles par programmation au moment de l’exécution. Vous pouvez ajouter ces contrôles par programmation à tout document ou feuille de calcul ouvert\(e\) au moment de l’exécution dans un complément VSTO pour Excel ou Word.  
  
 Pour plus d'informations, consultez [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Utilisation des contrôles Windows Forms  
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
  
## Ajout de contrôles Windows Forms par programmation  
 Vous pouvez ajouter des contrôles Windows Forms à des documents Word et des feuilles de calcul Excel au moment de l’exécution. Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] fournit des méthodes d’assistance pour ajouter les contrôles Windows Forms les plus courants. Ces méthodes d’assistance vous permettent d’ajouter rapidement des contrôles à votre document Office et d’accéder à la fonctionnalité Windows Forms et Office combinée de ces contrôles.  
  
 Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## Utilisation de contrôles Windows Forms dans des projets au niveau du document  
 Certains aspects liés à l’utilisation des contrôles Windows Forms sur les documents sont uniques aux projets au niveau du document, qui vous permettent de concevoir l’interface utilisateur de votre document en utilisant le concepteur Visual Studio.  
  
### Création de contrôles utilisateur personnalisés  
 Vous pouvez ajouter un contrôle utilisateur à votre projet, puis l’ajouter à la **Boîte à outils**. Vous pouvez ensuite faire glisser le contrôle utilisateur directement sur votre document, comme vous le feriez pour y ajouter un contrôle Windows Forms. Notez les points suivants lors de la création de contrôles utilisateur :  
  
-   Ne créez pas un contrôle utilisateur **sealed**. Lorsque vous faites glisser le contrôle sur votre document, Visual Studio génère une classe wrapper dérivée du contrôle utilisateur pour l’étendre et prendre en charge son utilisation dans le document. Si le contrôle utilisateur est **sealed**, Visual Studio ne peut pas générer la classe wrapper.  
  
-   L’attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> des contrôles utilisateur doit avoir la valeur **true**. Par défaut, pour les contrôles utilisateur créés à l’intérieur d’un projet Office cet attribut a la valeur **true**, mais il est possible que ce ne soit pas le cas pour les contrôles utilisateur qui font partie de projets extérieurs.  
  
-   Après avoir ajouté un contrôle utilisateur au document, ne renommez pas et supprimez pas la classe <xref:System.Windows.Forms.UserControl> du projet. Si vous devez modifier le nom d’un contrôle utilisateur, vous devez tout d’abord le supprimer du document, puis le rajouter après avoir modifié le nom.  
  
### Réorganisation des contrôles au moment du design  
 Si vous ajoutez plusieurs contrôles à vos documents Word et Excel au moment du design, vous pouvez rapidement définir l’alignement de tous les contrôles sélectionnés à l’aide des barres d’outils **Microsoft Office Word** et **Microsoft Office Excel** dans Visual Studio. Ces barres d’outils sont disponibles uniquement quand un document ou une feuille de calcul est ouvert\(e\) dans le concepteur.  
  
 Quand vous sélectionnez plusieurs contrôles dans le concepteur, vous pouvez utiliser les boutons suivants sur ces barres d’outils pour réorganiser les contrôles :  
  
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
  
### Empêcher des données anciennes d’apparaître dans les classeurs Excel pendant le chargement  
 Lorsque vous ajoutez des contrôles Windows Forms à des documents ou des feuilles de calcul au moment du design, les contrôles restent dans le document quand l’utilisateur le ferme. Les contrôles ajoutés au moment du design sont également appelés *contrôles statiques*.  
  
 Quand vous ouvrez un classeur Excel qui contient des contrôles statiques, il affiche une bitmap du contrôle dans un contrôle ActiveX jusqu’à ce que le code de personnalisation s’exécute et charge le contrôle proprement dit. Excel crée cette bitmap et la stocke dans le classeur chaque fois que celui\-ci est enregistré. La bitmap affiche le contrôle tel qu’il apparaissait la dernière fois que le classeur a été enregistré, y compris les données affichées par le contrôle. Pour plus d’informations sur le contrôle ActiveX qui contient des contrôles Windows Forms et des bitmaps, consultez [Limitations des contrôles Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
 Dans certaines conditions, par exemple lorsque l’utilisateur ouvre le classeur en mode Création, le code n’est pas chargé et seule la bitmap est affichée. En outre, si l’utilisateur ouvre le classeur sur un ordinateur sur lequel le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] n’est pas installé, la personnalisation ne peut pas s’exécuter pour charger les contrôles et seule la bitmap du contrôle est visible. Vous devez toujours supprimer les informations personnelles des contrôles dans les classeurs avant de les enregistrer et de les envoyer à un autre utilisateur, pour éviter toute divulgation involontaire.  
  
### Mise en correspondance de la taille de contrôle et de la taille de cellule sur une feuille de calcul Excel  
 Vous pouvez configurer le contrôle pour qu’il soit redimensionné automatiquement quand la taille de la cellule parente change. Pour plus d'informations, consultez [Comment : redimensionner des contrôles dans des cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### Ajout de composants partagés par toutes les feuilles de calcul  
 Vous pouvez ajouter des composants que vous souhaitez partager parmi toutes les feuilles de calcul, comme un <xref:System.Data.DataSet>, au Concepteur de classeurs plutôt qu’aux feuilles de calcul. Le composant apparaîtra dans la barre d’état des composants.  
  
### Formule pour incorporer des contrôles dans une feuille de calcul Excel  
 Quand vous sélectionnez un contrôle dans Excel, vous voyez **\=EMBED\("WinForms.Control.Host",""\)** dans la **Barre de formule**. Ce texte est nécessaire et ne doit pas être supprimé.  
  
### Style de disposition des contrôles dans un document Word  
 Quand vous ajoutez un contrôle au document Word dans un projet au niveau du document à l’aide du concepteur Visual Studio, le contrôle est aligné avec le texte. Pour modifier le style de disposition du contrôle, cliquez avec le bouton droit sur le contrôle, puis cliquez sur **Format de contrôle**. Sélectionnez un style d’habillage dans la page **Disposition** de la boîte de dialogue **Format d’objet**.  
  
 Quand vous ajoutez un contrôle à un document Word au moment de l’exécution, vous pouvez spécifier son style de disposition à l’aide de différentes surcharges de méthode `Add`\<*classe\_de\_contrôle*\> de la classe <xref:Microsoft.Office.Tools.Word.ControlCollection> :  
  
-   Pour aligner le contrôle avec le texte, utilisez une surcharge qui accepte un <xref:Microsoft.Office.Interop.Word.Range> qui spécifie l’emplacement du contrôle.  
  
-   Pour ajouter le contrôle en tant que forme flottante, utilisez une surcharge qui accepte les coordonnées de gauche et supérieure du contrôle.  
  
 Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Si vous ouvrez un modèle Word dans le concepteur Visual Studio, les contrôles non inline sur le modèle ne seront peut\-être pas visibles, car Visual Studio ouvre le modèle en mode **Normal**. Pour afficher les contrôles, basculez en mode **Page**.  
  
### Contrôles en dehors du corps de document principal  
 Les contrôles Windows Forms ne sont pas pris en charge dans un en\-tête ou un pied de page, ni dans un sous\-document.  
  
### Ajout de composants au moment du design  
 Certains contrôles ou composants ne sont pas visibles dans le document, mais sont plutôt affichés dans une barre d’état des composants. Visual Studio fournit une barre d’état des composants pour chaque fenêtre de document. La barre d’état des composants est affichée à l’écran uniquement s’il existe des composants dans le document.  
  
## Voir aussi  
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md)   
 [contrôles Windows Forms](../Topic/Windows%20Forms%20Controls.md)   
 [Limitations des contrôles Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Comment : redimensionner des contrôles dans des cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Comment : masquer des contrôles sur des feuilles de calcul lors de l'impression](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Procédure pas à pas : modification de la mise en forme d'une feuille de calcul à l'aide de contrôles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Procédure pas à pas : modification de la mise en forme d'un document à l'aide de contrôles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)   
 [Procédure pas à pas : affichage de texte dans une zone de texte d'une feuille de calcul à l'aide d'un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Procédure pas à pas : affichage de texte dans une zone de texte d'un document à l'aide d'un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)   
 [Limitations des contrôles Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [Procédure pas à pas : mise à jour d'un graphique dans un document à l'aide de cases d'option](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)   
 [Procédure pas à pas : mise à jour d'un graphique dans une feuille de calcul à l'aide de cases d'option](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  