---
title: Utilisation du GPU | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 957fed3c-4ded-4e05-87c6-ccc33de65349
caps.latest.revision: 4
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: e9a05d008f671fb79d6813a14c594b82f27697e3
ms.openlocfilehash: 1613943840c79028e3c60db0f54a73243eb3948c
ms.lasthandoff: 03/27/2017

---
# <a name="gpu-usage"></a>Utilisation du GPU
Servez-vous de l'outil Utilisation du GPU dans le hub Performances et diagnostics de Visual Studio pour mieux comprendre l'utilisation du matériel de pointe par votre application Direct3D. Vous pouvez l'utiliser pour déterminer si les performances de votre application sont liées à l'UC ou au GPU, et mieux comprendre comment tirer parti de la plateforme matérielle plus efficacement. L'outil Utilisation du GPU prend en charge les applications Direct3D 12, Direct3D 11 et Direct3D 10. Il ne prend pas en charge les autres API graphiques telles que Direct2D ou OpenGL.  
  
 Voici la fenêtre **Rapport d’utilisation du GPU** :  
  
 ![Rapport d’utilisation du GPU, avec les chronologies GPU et UC](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")  
  
## <a name="requirements"></a>Spécifications  
 Voici les conditions requises pour l'outil Utilisation du GPU, en plus de celles de Graphics Diagnostics.  
  
-   GPU et pilote qui prennent en charge l'instrumentation de minutage nécessaire.  
  
    > [!NOTE]
    >  Pour plus d’informations sur le matériel et les pilotes pris en charge, consultez [Prise en charge du matériel et des pilotes](#hwsupport) à la fin de ce document.  
  
 Pour plus d’informations sur les conditions requises par l’exécution de Graphics Diagnostics, consultez [Prise en main](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md).  
  
## <a name="using-the-gpu-usage-tool"></a>Emploi de l'outil Utilisation du GPU  
 Quand vous exécutez votre application dans l'Outil utilisation du GPU, Visual Studio crée une session de diagnostic qui représente sous forme graphique des informations générales relatives aux performances de rendu et à l'utilisation du GPU en temps réel de votre application.  
  
#### <a name="to-start-the-gpu-usage-tool"></a>Pour démarrer l'outil Utilisation du GPU :  
  
1.  Dans le menu principal, choisissez **Déboguer**, puis **Performances et diagnostics** (clavier : appuyez sur Alt+F2).  
  
2.  Dans le hub Performances et diagnostics, cochez la case en regard de l’option **Utilisation du GPU**. Vous pouvez éventuellement cocher les cases en regard des autres outils qui vous intéressent. Vous pouvez exécuter simultanément plusieurs outils du hub Performances et diagnostics pour obtenir une image plus complète des performances de votre application.  
  
     ![Choisissez les outils de diagnostic que vous souhaitez utiliser.](media/gfx_diag_diagsession_tools.png "gfx_diag_diagsession_tools")  
  
    > [!NOTE]
    >  Tous les outils du hub Performances et diagnostics peuvent être utilisés en même temps.  
  
3.  Choisissez le bouton **Démarrer** bleu au bas du hub Performances et diagnostics pour exécuter votre application à l’aide des outils que vous avez sélectionnés.  
  
 Les informations générales qui s'affichent en temps réel incluent le minutage de frame, la fréquence d'images et l'utilisation du GPU. Chacune de ces informations est représentée graphiquement de manière indépendante, mais selon une échelle de temps commune, ce qui vous permet d'associer facilement les informations entre elles.  
  
 Les graphiques **Durée de frame (ms)** et **Images par seconde (FPS)** contiennent deux lignes rouges horizontales qui représentent les performances cibles de 60 et 30 frames par seconde. Dans le graphique **Durée de frame**, votre application dépasse les performances cibles quand le graphique est en dessous de la ligne, et n’atteint pas les performances cibles quand le graphique est au-dessus de la ligne. Pour le graphique Images par seconde, la situation est inversée. Votre application dépasse les performances cibles quand le graphique est au-dessus de la ligne, et n’atteint pas les performances cibles quand le graphique est en dessous de la ligne. Ces graphiques servent principalement à obtenir une idée générale des performances de votre application, et à identifier les ralentissements dont vous souhaitez peut-être connaître l'origine (par exemple, une chute soudaine de la fréquence d'images ou un pic d'utilisation du GPU).  
  
 Pendant que votre application s'exécute dans l'outil Utilisation du GPU, la session de diagnostic collecte également des informations détaillées sur les événements graphiques exécutés sur le GPU. Ces informations sont utilisées pour générer un rapport plus précis de la manière dont votre application utilise le matériel. Dans la mesure où ce rapport prend un certain temps pour générer les résultats à partir des informations collectées, il est disponible uniquement à la fin de la collecte d'informations de la session de diagnostic.  
  
 Quand vous souhaitez examiner plus attentivement un problème de performances ou d'utilisation, arrêtez de collecter les informations de performances pour que le rapport puisse être généré.  
  
#### <a name="to-generate-and-view-the-gpu-usage-report"></a>Pour générer et afficher le rapport d'utilisation du GPU :  
  
1.  Dans la partie inférieure de la fenêtre de session de diagnostic, choisissez le lien **Arrêter la collecte** ou appuyez sur **Arrêter** en haut à gauche.  
  
     ![Collectez les informations de minutage GPU et UC.](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")  
  
2.  Dans la partie supérieure du rapport, sélectionnez une section dans l'un des graphiques qui illustre le problème à examiner. Votre sélection peut durer jusqu'à 3 secondes. Le début des sections plus longues est tronqué.  
  
     ![Postcollection, sélectionner une plage pour afficher les détails](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")  
  
3.  Dans la partie inférieure du rapport, choisissez le lien **Afficher les détails** du message **...cliquez ici pour afficher les détails de l’utilisation du GPU pour cette plage** afin d’afficher une chronologie détaillée de votre sélection.  
  
     ![Postcollection, avec la plage sélectionnée](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")  
  
 Cela entraîne l'ouverture d'un nouveau document avec onglets qui contient le rapport. Le rapport Utilisation du GPU vous aide à identifier le moment où un événement graphique démarre sur l'UC et où il atteint le GPU, ainsi que sa durée d'exécution par le GPU. Ces informations peuvent vous aider à identifier les goulots d’étranglement et les opportunités d’augmentation du parallélisme dans votre code.  

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>Exporter vers GPUView ou Windows Performance Analyzer
À partir de Visual Studio 2017, vous pouvez ouvrir ces données avec [GPUView](https://msdn.microsoft.com/library/windows/desktop/ff570133(v=vs.85).aspx) et [Windows Performance Analyzer](https://msdn.microsoft.com/windows/hardware/commercialize/test/wpt/windows-performance-analyzer) en cliquant sur les liens **Ouvrir dans GpuView** ou **Ouvrir dans WPA** situés en bas à droite de la session de diagnostic.

![Ouvrir dans...](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="using-the-gpu-usage-report"></a>Emploi du rapport Utilisation du GPU  
 La partie supérieure du rapport Utilisation du GPU affiche les chronologies de l'activité de traitement de l'UC, de l'activité de rendu du GPU et de l'activité de copie du GPU. Ces chronologies sont séparées par des barres verticales, gris clair, représentant le vsync de l’affichage. La fréquence des barres correspond à la fréquence de rafraîchissement de l’un des affichages (sélectionné à l’aide de la liste déroulante **Affichage**) à partir desquels les données d’utilisation du GPU ont été collectées. Dans la mesure où l'affichage peut avoir une fréquence de rafraîchissement plus élevée que les performances cibles de votre application, il n'existe peut-être pas de relation 1 à 1 entre le vsync et la fréquence d'images que votre application doit atteindre. Pour atteindre ses performances cibles, une application doit achever tous les traitements, effectuer le rendu et exécuter un appel de Present() au niveau de la fréquence d'images ciblée. Toutefois, le frame rendu ne s'affichera pas jusqu'au prochain vsync après Present().  
  
 La partie inférieure affiche une liste des événements graphiques qui se sont produits pendant l'exécution du rapport.  
  
 Voici la fenêtre **Rapport d’utilisation du GPU** :  
  
 ![Rapport d’utilisation du GPU, avec les chronologies GPU et UC](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")  
  
 Si vous sélectionnez l’un des événements dans la partie inférieure du rapport, cela entraîne le placement d’un marqueur au niveau des événements correspondants dans les chronologies appropriées, en général un événement sur un thread d’UC qui représente l’appel d’API et un autre événement sur l’une des chronologies GPU qui représente la fin de l’achèvement de la tâche par le GPU. De même, si vous sélectionnez l'un des événements d'une chronologie, cela entraîne la mise en surbrillance de l'événement correspondant dans la partie inférieure du rapport. Quand vous effectuez un zoom arrière des chronologies dans la partie supérieure du rapport, seuls les événements les plus longs sont visibles. Pour afficher les événements qui ont une durée plus courte, effectuez un zoom avant des chronologies en appuyant sur la touche Ctrl et en utilisant la roulette de votre dispositif de pointage, ou via le contrôle de mise à l'échelle situé dans le coin inférieur gauche du panneau supérieur. Vous pouvez également faire glisser le contenu du panneau de chronologie pour parcourir les événements enregistrés.  
  
 Pour faciliter vos recherches, vous pouvez filtrer le rapport d'utilisation du GPU en fonction des noms de processus, des ID de thread et du nom d'événement. En outre, vous pouvez choisir la fréquence de rafraîchissement de l'affichage qui détermine les lignes vsync, et vous pouvez trier les événements hiérarchiquement si votre application utilise l'interface ID3DUserDefinedAnnotation pour regrouper les commandes de rendu.  
  
 Voici des détails supplémentaires :  
  
|Contrôle de filtre|Description|  
|--------------------|-----------------|  
|**Process**|Nom du processus qui vous intéresse. Tous les processus qui ont utilisé le GPU pendant la session de diagnostic sont inclus dans cette liste déroulante. La couleur associée au processus dans cette liste déroulante est la couleur de l’activité du thread dans les chronologies ci-dessous.|  
|**Thread**|ID de thread qui vous intéresse. Dans une application multithread, cela peut vous aider à isoler les threads particuliers qui appartiennent au processus qui vous intéresse. Les événements associés au thread sélectionné sont mis en surbrillance dans chaque chronologie.|  
|**Afficher**|Numéro de l’affichage dont la fréquence de rafraîchissement est indiquée **Remarque :** Certains pilotes peuvent être configurés pour présenter plusieurs affichages physiques sous forme d’un affichage virtuel unique, de grande taille. Vous ne verrez peut-être qu'un seul affichage dans la liste, même si l'ordinateur possède plusieurs affichages attachés.|  
|**Filtrer**|Mots clés qui vous intéressent. Les événements de la partie inférieure du rapport incluent uniquement ceux qui correspondent complètement ou partiellement à un mot clé. Vous pouvez spécifier plusieurs mots clés en les séparant par des virgules.|  
|**Tri des hiérarchies**|Case à cocher qui indique si les hiérarchies d'événements (définies via des marqueurs utilisateur) sont conservées ou ignorées.|  
  
 La liste des événements dans la partie inférieure du rapport d'utilisation du GPU affiche les détails de chaque événement.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Nom de l’événement**|Nom de l'événement graphique. Un événement correspond généralement à un événement dans une chronologie de thread d'UC et à un événement dans une chronologie de GPU.<br /><br /> Des noms d'événements peuvent être « non attribués » si la fonctionnalité d'utilisation du GPU n'a pas pu déterminer le nom d'un événement. Pour plus d'informations, voir la remarque sous ce tableau.|  
|**Début UC (ns)**|Heure à laquelle l'événement a débuté sur l'UC en appelant une API Direct3D. Le temps est mesuré en nanosecondes, par rapport au moment où l'application a démarré.|  
|**Début GPU (ns)**|Heure à laquelle l'événement a débuté sur le GPU. Le temps est mesuré en nanosecondes, par rapport au moment où l'application a démarré.|  
|**Durée GPU (ns)**|Durée d'exécution de l'événement sur le GPU, en nanosecondes.|  
|**Nom du processus**|Nom de l'application d'où provient l'événement.|  
|**ID de thread**|ID de thread d'où provient l'événement.|  
  
> [!IMPORTANT]
>  Windows 8.1 est obligatoire pour l'attribution d'événement. En outre, si votre GPU ou pilote ne prend pas en charge les fonctionnalités d'instrumentation nécessaires, tous les événements s'affichent comme étant « non attribués ». Veillez à mettre à jour votre GPU/pilote, puis réessayez si vous rencontrez ce problème. Pour plus d’informations, consultez [Prise en charge du matériel et des pilotes](#hwsupport) ci-dessous.  
  
## <a name="gpu-usage-settings"></a>Paramètres d'utilisation du GPU  
 Vous pouvez configurer l'outil Utilisation du GPU pour reporter la collecte des informations de profilage, au lieu de commencer à collecter les informations dès le démarrage de l'application. Dans la mesure où la taille des informations de profilage peut être significative, cela s'avère utile de savoir que le ralentissement des performances de votre application ne se reproduira pas avant longtemps.  
  
#### <a name="to-postpone-profiling-from-the-start-of-the-app"></a>Pour reporter le profilage au démarrage de l'application :  
  
1.  Dans le menu principal, choisissez **Déboguer**, puis **Performances et diagnostics** (clavier : appuyez sur Alt+F2).  
  
2.  Dans le hub Performances et diagnostics, suivez le lien **Paramètres** à côté de l’option **Utilisation du GPU**.  
  
3.  Sous **Configuration du profilage GPU**, dans la page de propriétés **Général**, décochez la case **Commencer le profilage au démarrage de l’application** pour reporter le profilage.  
  
     ![Configurer le moment du démarrage de la collecte de données d’utilisation du GPU](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")  
  
> [!IMPORTANT]
>  Le report du profilage n'est pas pris en charge actuellement pour les applications Direct3D 12.  
  
 Quand vous reportez la collection des informations de profilage à l’aide de ce paramètre, un lien supplémentaire devient disponible dans la partie inférieure de la fenêtre de l’outil Utilisation du GPU au moment où vous exécutez votre application dans l’outil Utilisation du GPU. Pour commencer à collecter des informations de profilage, choisissez le lien **Démarrer** dans le message **Commencer à collecter des données détaillées d’utilisation GPU supplémentaires**.  
  
##  <a name="hwsupport"></a> Prise en charge du matériel et des pilotes  
 Le matériel et les pilotes GPU suivants sont pris en charge :  
  
|Fournisseur|Description du GPU|Version de pilote nécessaire|  
|------------|---------------------|-----------------------------|  
|Intel®|4e génération des processeurs Intel® Core ("Haswell")<br /><br /> -   Intel® HD Graphics (GT1)<br />-   Intel® HD Graphics 4200 (GT2)<br />-   Intel® HD Graphics 4400 (GT2)<br />-   Intel® HD Graphics 4600 (GT2)<br />-   Intel® HD Graphics P4600 (GT2)<br />-   Intel® HD Graphics P4700 (GT2)<br />-   Intel® HD Graphics 5000 (GT3)<br />-   Intel® Iris™ Graphics 5100 (GT3)<br />-   Intel® Iris™ Pro Graphics 5200 (GT3e)|-- (utilisez les derniers pilotes)|  
|AMD®|La plupart, à partir d'AMD Radeon™ HD série 7000 (sauf AMD Radeon™ HD 7350-7670)<br /><br /> GPU AMD Radeon™, GPU AMD FirePro™ et accélérateurs GPU AMD FirePro incluant l'architecture Graphics Core Next (GCN).<br /><br /> Unités de traitement accéléré (APU) AMD® série E et AMD série A incluant l'architecture Graphics Core Next (GCN) - ('Kaveri', 'Kabini', 'Temash', 'Beema', 'Mullins')|14.7 RC3 ou version supérieure|  
|NVIDIA®|La plupart, à partir de NVIDIA® GeForce® série 400.<br /><br /> GPU NVIDIA® GeForce®, GPU NVIDIA Quadro® et accélérateurs GPU NVIDIA® Tesla™ incluant l'architecture Fermi™, Kepler™ ou Maxwell™.|343.37 ou version supérieure|  
  
 Les configurations à plusieurs GPU, telles que NVIDIA® SLI™ et AMD Crossfire™, ne sont pas prises en charge pour l'instant. Les configurations graphiques hybrides, telles que NVIDIA® Optimus™ et AMD Enduro™, sont prises en charge.  
  
## <a name="see-also"></a>Voir aussi  
  
-   [Résoudre les problèmes graphiques complexes liés à votre jeu à l’aide des outils DirectX (vidéo)](http://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)  
-   [Outil Utilisation du GPU dans Visual Studio (vidéo)](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)  
-   [Outil Utilisation du GPU dans Visual Studio 2013 Update 4 CTP1 (blog)](http://blogs.msdn.com/b/vcblog/archive/2014/09/05/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1.aspx)  
-   [Utilisation du GPU pour DirectX dans Visual Studio (blog)](http://blogs.msdn.com/b/ianhu/archive/2014/12/16/gpu-usage-for-directx-in-visual-studio.aspx)
- [GPUView](https://msdn.microsoft.com/library/windows/desktop/ff570133(v=vs.85).aspx) 
- [Windows Performance Analyzer](https://msdn.microsoft.com/windows/hardware/commercialize/test/wpt/windows-performance-analyzer)
