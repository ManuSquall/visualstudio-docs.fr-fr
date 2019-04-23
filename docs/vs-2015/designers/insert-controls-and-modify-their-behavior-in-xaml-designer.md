---
title: Insérer des contrôles et modifier leur comportement dans le concepteur XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e36b7cef0c24367292f7f9e60b86eb9138b12a64
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082943"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Insérer des contrôles et modifier leur comportement dans le concepteur XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les contrôles permettent aux utilisateurs d'interagir avec votre application. Elles peuvent s'avérer utiles pour collecter des informations et effectuer des actions, comme animer un objet ou interroger une source de données.  
  
 **Dans cette rubrique :**  
  
- [Ajouter des contrôles à la planche graphique](#Insert)  
  
- [Rendre les contrôles actifs](#Modify)  
  
## <a name="Insert"></a> Ajouter des contrôles à la planche graphique  
 Vous pouvez faire glisser des contrôles du panneau **Composants** vers la **planche graphique**, puis les modifier dans la fenêtre **Propriétés** .  
  
 ![Blend &#45; Assets &#45; FlipView](../designers/media/blend-assetsflipview-xaml.png "blend_AssetsFlipView_XAML")  
  
 Ces vidéos vous montrent comment utiliser quelques-uns des contrôles les plus courants.  
  
|Contrôle|Regardez une courte vidéo :|  
|-------------|-------------------------|  
|`Menu`![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c-0b2b-4253-ac57-b86fcb8c9591")|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Add the controls (Ajouter les contrôles)](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|  
|`Button`![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779-a68f-436b-b834-a91b7995a3ec")|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Design a button (Concevoir un bouton)](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|  
|`Textblock`![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963-00f7-4a33-abcd-b0849edebada")|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Add images to a textblock (Ajouter des images à un bloc de texte)](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|  
|`Slider`![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92-3c74-4218-815c-e98c930ac189")|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Build a Slider with a ToolTip (Créer un curseur avec une info-bulle)](http://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|  
|`GridSplitter`![](../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be")|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Work with a GridSplitter (Utiliser un contrôle GridSplitter)](https://www.youtube.com/watch?v=bf4t6c8ms2w)|          

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Créer un contrôle à partir d’une image, d’une forme ou d’un tracé  
 Vous pouvez transformer n'importe quel objet en contrôle.  
  
 ![Boîte de dialogue Créer un contrôle dans Blend](../designers/media/blend-makeintocontrol-xaml.png "blend_MakeIntoControl_XAML")  
  
 Par exemple, imaginez une image de téléviseur au milieu d'une page. Vous pourriez créer des contrôles à partir de petites images représentant des boutons de téléviseur. Les utilisateurs pourraient ensuite cliquer sur ces boutons pour changer de chaîne.  
  
 Cela serait possible, car les boutons seraient dès lors des contrôles. Les contrôles permettent de répondre aux interactions de l'utilisateur (dans ce cas, le clic de l'utilisateur sur un bouton).  
  
 Pour créer un contrôle, sélectionnez un objet. Ensuite, dans le menu **Outils** , cliquez sur **Créer un contrôle**.  
  
## <a name="Modify"></a> Rendre les contrôles actifs  
 Les contrôles peuvent effectuer des actions quand les utilisateurs interagissent avec eux. Par exemple, ils peuvent démarrer une animation, mettre à jour une source de données ou lire une vidéo.  
  
 Pour rendre des contrôles actifs, vous devez utiliser des *déclencheurs*, des *comportements*et des *événements* .  
  
### <a name="triggers"></a>déclencheurs  
 Un *déclencheur* modifie une propriété ou effectue une tâche en réponse à un événement ou à une modification apporté à une autre propriété. Par exemple, vous pouvez faire en sorte qu'un bouton change de couleur quand les utilisateurs le pointent avec la souris.  
  
 ![Volet Déclencheurs](../designers/media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [ajouter un déclencheur de propriété](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).  
  
### <a name="behaviors"></a>comportements  
 Un *comportement* est un ensemble de code réutilisable. Il permet de faire un peu plus que modifier les propriétés. Il permet d'effectuer certaines actions, comme interroger un service de données. Blend en propose une petite collection, mais vous pouvez en ajouter d'autres. Faites glisser un comportement sur un objet dans la planche graphique, puis personnalisez-le en définissant des propriétés.  
  
 ![FluidMoveBehavior dans le panneau Propriétés](../designers/media/b4-fluidmovebehaviorproperties-sample.png "b4_FluidMoveBehaviorProperties_Sample")  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [conseils sur Blend : Intro to using behaviors Part 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).  
  
### <a name="events"></a>Événements  
 Pour un maximum de souplesse, traitez un *événement*. Vous devrez écrire un peu de code.  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [ajouter un événement de souris](https://www.youtube.com/watch?v=2PMxAlb-x_E).
