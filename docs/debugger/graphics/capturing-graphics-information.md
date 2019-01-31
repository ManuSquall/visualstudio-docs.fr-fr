---
title: Capture d’informations graphiques | Microsoft Docs
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f6bbaf9a387a43accfd779c9583687ec98b1813
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952429"
---
# <a name="capturing-graphics-information"></a>Capture d'informations graphiques
Capturez les informations graphiques de votre application Direct3D pour pouvoir diagnostiquer les problèmes de performances et de rendu à l'aide de Visual Studio Graphics Analyzer.  
  
## <a name="capturing-graphics-information"></a>Capture d'informations graphiques  
 La capture d'informations graphiques est un processus en deux étapes. Vous devez tout d'abord exécuter l'application dans Graphics Diagnostics, puis spécifier un ou plusieurs types de frames à partir desquels capturer des informations détaillées.  
  
### <a name="to-run-your-app-under-graphics-diagnostics"></a>Pour exécuter l’application dans Graphics Diagnostics  
  
- Dans la barre de menus, choisissez **déboguer**, **Graphics**, **démarrer le débogage graphique**. (Clavier : Appuyez sur Alt + F5)  
  
- Sur le **Graphics** barre d’outils, choisissez le **démarrer le débogage graphique** bouton.  
  
  Lorsqu’une application s’exécute dans Graphics Diagnostics, certains types d’informations graphiques sont systématiquement capturés. Notamment l’installation de périphérique, la création de chaîne de permutation, la création d’objets graphiques et de ressources, et d’autres événements significatifs qui affectent plusieurs frames. En même temps, vous pouvez capturer des informations détaillées sur des frames spécifiques. Cela inclut des appels de dessin et des distributions de nuanceur de calcul, ainsi que des objets Direct3D et des ressources qui les prennent en charge.  
  
### <a name="to-capture-a-frame"></a>Pour capturer un frame  
  
- Dans Visual Studio, sur le **Graphics** barre d’outils, cliquez sur le **capturer le Frame** bouton ![Graphics capture l’icône du bouton](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics").  
  
- Sur le clavier, appuyez sur la touche Impr. écran.
  
  > [!NOTE]
  >  Quand une application s’exécute sous **Graphics Diagnostics**, la touche Impr. écran sert uniquement à capturer un frame d’informations graphiques. Elle n’effectue pas sa fonction habituelle. Cela reste en vigueur jusqu'à ce que vous ayez arrêté de capturer des informations graphiques (en général en arrêtant le débogage ou en quittant l'application normalement) même si une autre application est dans le focus.  
  
- Dans l’interface de capture Visual Studio, choisissez le bouton **Capturer le frame** situé sous la chronologie **Session de diagnostic**. Sinon, choisissez le grand bouton **Capturer le frame** situé sous la zone **Frames par seconde** et à la droite des frames précédemment capturés. Les deux boutons sont mis en évidence dans l'image ci-dessous.  
  
   ![Capturer des frames à l'aide de l'outil Utilisation du GPU.](media/pix_gpu_usage_tool_capture_frame.png)  
  
   Une fois que vous êtes prêt à examiner les frames que vous avez capturés, démarrez **Visual Studio Graphics Analyzer** en suivant le lien **Frame...** au-dessus des images miniatures, ou en double-cliquant sur la miniature.  
  
  Seuls les frames entiers peuvent être capturés. Par conséquent, quand vous lancez une capture, il s’agit en fait des informations graphiques provenant du frame suivant qui sont enregistrées. L'enregistrement démarre dès que le frame dans lequel vous avez lancé la capture est affiché et se termine lorsque le frame capturé est affiché. Vous pouvez capturer autant de frames que vous souhaitez tant que l’application s’exécute dans Graphics Diagnostics. Si vous ne capturez pas frame, le journal de graphisme est ignoré.  
  
  Durant la capture de frames, Visual Studio affiche la fenêtre de session de diagnostic (.diagsession). Si vous fermez cette fenêtre, arrêtez le débogage ou fermez l’application, vous ne pouvez plus capturer de frames supplémentaires dans ce journal. Pour capturer des informations graphiques supplémentaires, vous devez réexécuter l’application Graphics Diagnostics et démarrer une nouvelle session de diagnostic.  
  
### <a name="graphics-diagnostics-capture-options"></a>Options de capture de Graphics Diagnostics  
 Vous pouvez configurer la capture pour collecter les piles des appels de tous les événements graphiques ou d'une partie limitée de ces derniers, désactiver le HUD de capture, et activer ou désactiver le mode de compatibilité de capture.  
  
#### <a name="to-configure-graphics-diagnostics-capture-options"></a>Pour configurer les options de capture de Graphics Diagnostics  
  
1.  Dans la barre de menus, choisissez Outils, Options. La boîte de dialogue Options s'affiche.  
  
2.  Dans la liste des catégories d’options sur la gauche, choisissez Graphics Diagnostics, puis configurez les options Graphics Diagnostics de votre choix.  
  
     **Collecter les piles des appels durant la capture (ralentit la capture)**  
     Cochez cette case pour collecter les piles des appels. Par défaut, les piles des appels ne sont pas collectées. Pour capturer les piles des appels, vérifiez que la case **Collecter les piles des appels durant la capture (ralentit la capture)** est cochée pour permettre la collecte, puis définissez l’option **pour les marqueurs de dessin, de répartition, de présentation et de performances** (par défaut) pour collecter uniquement les piles des appels les plus importantes, ou l’option **pour tout** afin de collecter toutes les piles des appels. Pour arrêter plus tard de collecter les piles des appels, décochez la case **Collecter les piles des appels durant la capture (ralentit la capture)**.  
  
     **Désactiver le HUD dans le jeu durant la capture**  
     Cochez cette case pour désactiver le HUD superposé qu’une application en cours d’exécution sous Graphics Diagnostics affiche généralement. Décochez cette case pour afficher le HUD superposé.  
  
     **Capture en mode de compatibilité**  
     Cochez cette case pour capturer les informations graphiques en mode de compatibilité. Par défaut, la capture est effectuée en mode de compatibilité. En mode de compatibilité, Direct3D ne signale pas que le GPU prend en charge des fonctionnalités supplémentaires au-delà de celles définies dans le niveau de fonctionnalité de base. Cela empêche l'application capturée d'utiliser les extensions spécifiques au matériel du GPU sur lequel elle est capturée. En outre, cela garantit que le journal de graphisme peut être lu à l'aide de n'importe quel GPU prenant en charge un niveau de fonctionnalité identique ou supérieur. Décochez cette case pour désactiver le mode de compatibilité. Les journaux capturés quand le mode de compatibilité est désactivé ne peuvent pas être lus sur un GPU qui ne prend pas en charge les mêmes fonctionnalités supplémentaires que celles utilisées par l’application durant la capture.  
  
     **Arrêter la capture si des erreurs de couches du SDK sont détectées**  
     Cochez cette case pour arrêter la capture immédiatement si des erreurs sont rencontrées.  
  
## <a name="capturing-graphics-information-remotely"></a>Capture d'informations graphiques à distance  
 Les informations graphiques peuvent être capturées à partir d'une application qui est exécutée sur un ordinateur local, un ordinateur ou un appareil distant. La capture distante est prise en charge pour les ordinateurs [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)] et les appareils [!INCLUDE[winblue_winrt_2](../includes/winblue_winrt_2_md.md)]. Pour capturer des informations graphiques à partir d’une application exécutée à distance, configurez votre projet pour le débogage distant et exécutez l’application dans Graphics Diagnostics comme décrit plus haut. L'application s'exécute sur l'ordinateur distant, les informations graphiques capturées sont stockées sur votre ordinateur de développement.  
  
 La façon dont vous configurez votre projet pour le débogage distant dépend du type d'application et du langage de programmation que vous utilisez. Pour plus d’informations sur la configuration du débogage à distance pour une application UWP, consultez [exécuter des applications UWP sur un ordinateur distant](../run-windows-store-apps-on-a-remote-machine.md). Pour plus d’informations sur la configuration du débogage à distance pour une application de bureau Windows, consultez [le débogage à distance](../remote-debugging.md).  
  
 Vous pouvez utiliser par la suite un ordinateur ou un appareil distant pour lire des informations graphiques, indépendamment de l'endroit où les informations ont été capturées. Pour plus d'informations, voir [Procédure : modifier l’ordinateur de lecture Graphics Diagnostics](how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="capturing-graphics-information-from-the-command-line"></a>Capture d'informations graphiques à partir de la ligne de commande  
 Vous pouvez capturer des informations graphiques à partir d'une application via un outil en ligne de commande. Cet outil, DXCap.exe, peut rapidement capturer et lire des informations graphiques sans passer par Visual Studio ou une capture par programmation. En particulier, vous pouvez utiliser DXCap.exe pour l'automatisation ou dans un environnement de test. Pour plus d’informations sur DXCap.exe, consultez [Outil en ligne de commande de capture](command-line-capture-tool.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : capture d’informations graphiques](walkthrough-capturing-graphics-information.md)