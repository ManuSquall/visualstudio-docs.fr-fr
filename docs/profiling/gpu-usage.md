---
title: Utilisation du GPU | Microsoft Docs
ms.date: 11/01/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f16a518542e8acab636da6e395fdfee8d7a25085
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969812"
---
# <a name="gpu-usage"></a>Utilisation du GPU

L’outil Utilisation du GPU dans le hub Performances et diagnostics de Visual Studio vous permet de mieux comprendre l’utilisation du matériel de pointe par votre application Direct3D. Il vous aide à déterminer si les performances de votre application sont liées à l’UC ou au GPU, et à mieux comprendre comment tirer parti plus efficacement du matériel de la plateforme. L'outil Utilisation du GPU prend en charge les applications Direct3D 12, Direct3D 11 et Direct3D 10. Il ne prend pas en charge les autres API graphiques telles que Direct2D ou OpenGL.

Cette capture d’écran montre la fenêtre **Rapport d’utilisation du GPU** :

![Rapport d’utilisation du GPU, avec les chronologies GPU et UC](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>Spécifications

Voici les conditions requises pour l’outil Utilisation du GPU, qui s’ajoutent à celles de Graphics Diagnostics.

- GPU et pilote qui prennent en charge l'instrumentation de minutage nécessaire.

  > [!NOTE]
  > Pour plus d’informations sur le matériel et les pilotes pris en charge, consultez [Prise en charge du matériel et des pilotes](#hwsupport) à la fin de ce document.

  Pour plus d’informations sur les conditions requises par l’exécution de Graphics Diagnostics, consultez [Prise en main](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md).

## <a name="using-the-gpu-usage-tool"></a>Emploi de l'outil Utilisation du GPU

 Quand vous exécutez votre application dans l’outil Utilisation du GPU, Visual Studio crée une session de diagnostic qui représente sous forme de graphiques en temps réel des informations générales relatives aux performances du rendu et à l’utilisation du GPU de votre application.

**Pour démarrer l’outil Utilisation du GPU :**

1. Dans le menu principal, choisissez **Déboguer**, puis **Performances et diagnostics** (clavier : appuyez sur Alt+F2).

2. Dans le hub Performances et diagnostics, cochez la case en regard de l’option **Utilisation du GPU**. Vous pouvez éventuellement cocher les cases en regard des autres outils qui vous intéressent. Vous pouvez exécuter simultanément plusieurs outils du hub Performances et diagnostics pour obtenir une image plus complète des performances de votre application.

    ![Choisissez les outils de diagnostic que vous souhaitez utiliser.](media/gfx_diag_diagsession_tools.png "gfx_diag_diagsession_tools")

   > [!NOTE]
   > Tous les outils du hub Performances et diagnostics peuvent être utilisés en même temps.

3. Choisissez le bouton **Démarrer** bleu au bas du hub Performances et diagnostics pour exécuter votre application à l’aide des outils que vous avez sélectionnés.

   Les informations générales qui s’affichent en temps réel incluent la chronologie des images, la fréquence d’images et l’utilisation du GPU. Chacune de ces informations est représentée graphiquement de façon indépendante, mais selon une échelle de temps commune, ce qui vous permet d’associer facilement les informations entre elles.

   Les graphiques **Durée de frame (ms)** et **Images par seconde (IPS)** contiennent deux lignes rouges horizontales qui représentent les performances cibles de 60 et de 30 images par seconde. Dans le graphique **Durée de frame**, votre application dépasse les performances cibles quand la courbe est en dessous de la ligne, et n’atteint pas la cible quand la courbe est au-dessus de la ligne. Pour le graphique Images par seconde, c’est le contraire : votre application dépasse les performances cibles quand la courbe est au-dessus de la ligne, et n’atteint pas la cible quand la courbe est en dessous de la ligne. Ces graphiques servent principalement à obtenir une idée générale des performances de votre application, et à identifier les ralentissements dont vous souhaitez peut-être connaître l’origine, par exemple une chute soudaine de la fréquence d’images ou un pic d’utilisation du GPU.

   Pendant que votre application s'exécute dans l'outil Utilisation du GPU, la session de diagnostic collecte également des informations détaillées sur les événements graphiques exécutés sur le GPU. Ces informations sont utilisées pour générer un rapport plus précis de la manière dont votre application utilise le matériel. Dans la mesure où ce rapport prend un certain temps pour générer les résultats à partir des informations collectées, il est disponible uniquement à la fin de la collecte d’informations de la session de diagnostic.

   Quand vous souhaitez examiner plus attentivement un problème de performances ou d'utilisation, arrêtez de collecter les informations de performances pour que le rapport puisse être généré.

**Pour générer et afficher le rapport d’utilisation du GPU :**

1. Dans la partie inférieure de la fenêtre de session de diagnostic, choisissez le lien **Arrêter la collecte** ou appuyez sur **Arrêter** en haut à gauche.

   ![Collectez les informations de minutage GPU et UC.](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. Dans la partie supérieure du rapport, sélectionnez une section dans l'un des graphiques qui illustre le problème à examiner. Votre sélection peut durer jusqu'à 3 secondes. Le début des sections plus longues est tronqué.

   ![Postcollection, sélectionner une plage pour afficher les détails](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. Dans la partie inférieure du rapport, choisissez le lien **Afficher les détails** du message **...cliquez ici pour afficher les détails de l’utilisation du GPU pour cette plage** afin d’afficher une chronologie détaillée de votre sélection.

   ![Postcollection, avec la plage sélectionnée](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

   Cette sélection ouvre un nouveau document avec onglets qui contient le rapport. Le rapport Utilisation du GPU vous aide à identifier le moment où un événement graphique démarre sur l’UC et où il atteint le GPU, ainsi que sa durée d’exécution par le GPU. Ces informations peuvent vous aider à identifier les goulots d’étranglement et les opportunités d’augmentation du parallélisme dans votre code.

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>Exporter vers GPUView ou Windows Performance Analyzer

À compter de Visual Studio 2017, vous pouvez ouvrir ces données avec [GPUView](/windows-hardware/drivers/display/using-gpuview) et [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer). Sélectionnez simplement les liens **Ouvrir dans GpuView** ou **Ouvrir dans l’outil d’activation de Windows** situés en bas à droite de la session de diagnostic.

![Ouvrir dans...](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="using-the-gpu-usage-report"></a>Emploi du rapport Utilisation du GPU

La partie supérieure du rapport Utilisation du GPU montre les chronologies de l’activité de traitement de l’UC, de l’activité de rendu du GPU et de l’activité de copie du GPU. Ces chronologies sont séparées par des barres verticales gris clair qui indiquent le VSync de l’affichage. La fréquence des barres correspond à la fréquence de rafraîchissement d’un des affichages (sélectionné dans la liste déroulante **Affichage**) à partir dans lesquels les données d’utilisation du GPU ont été collectées. Dans la mesure où l’affichage peut avoir une fréquence de rafraîchissement plus élevée que les performances cibles de votre application, il est possible qu’il n’existe pas de relation 1 à 1 entre le VSync et la fréquence d’images que votre application doit atteindre. Pour atteindre ses performances cibles, une application doit effectuer tous les traitements, effectuer le rendu et faire un appel de Present() à la fréquence d’images ciblée. L’image rendue ne s’affiche cependant pas avant le VSync suivant l’appel de Present().

La partie inférieure affiche une liste des événements graphiques qui se sont produits pendant l'exécution du rapport.

Voici la fenêtre **Rapport d’utilisation du GPU** :

![Rapport d’utilisation du GPU, avec les chronologies GPU et UC](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

Quand vous sélectionnez un événement dans la partie inférieure du rapport, un marqueur apparaît pour les événements correspondants dans les chronologies concernées. En règle générale, un événement sur un thread d’UC montre l’appel de l’API, tandis qu’un autre événement sur une des chronologies du GPU apparaît quand le GPU a terminé la tâche. De même, quand vous sélectionnez un événement dans une chronologie, le rapport met en évidence l’événement correspondant dans la partie inférieure du rapport. Quand vous effectuez un zoom arrière des chronologies dans la partie supérieure du rapport, seuls les événements les plus longs sont visibles. Pour afficher les événements qui ont une durée plus courte, effectuez un zoom avant des chronologies en appuyant sur la touche Ctrl et en utilisant la roulette de votre dispositif de pointage, ou via le contrôle de mise à l'échelle situé dans le coin inférieur gauche du panneau supérieur. Vous pouvez également faire glisser le contenu du panneau de chronologie pour parcourir les événements enregistrés.

Pour trouver plus facilement ce que vous cherchez, filtrez le rapport Utilisation du GPU sur les noms de processus, les ID de thread et le nom d’événement. En outre, vous pouvez choisir la fréquence d’actualisation de l’affichage qui détermine les lignes de VSync. Vous pouvez trier les événements hiérarchiquement si votre application utilise l’interface [ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) pour regrouper les commandes de rendu.

 Voici des détails supplémentaires :

|Contrôle de filtre|Description|
|--------------------|-----------------|
|**Process**|Nom du processus qui vous intéresse. Tous les processus qui ont utilisé le GPU pendant la session de diagnostic sont inclus dans cette liste déroulante. La couleur associée au processus dans cette liste déroulante est la couleur de l’activité du thread dans les chronologies ci-dessous.|
|**Thread**|ID de thread qui vous intéresse. Dans une application multithread, ces informations peuvent vous aider à isoler des threads particuliers qui appartiennent au processus qui vous intéresse. Les événements associés au thread sélectionné sont mis en surbrillance dans chaque chronologie.|
|**Afficher**|Numéro de l’affichage dont la fréquence de rafraîchissement est indiquée.**Remarque  :**  Certains pilotes peuvent être configurés pour présenter plusieurs affichages physiques sous forme d'un affichage virtuel unique, de grande taille. Vous ne verrez peut-être qu'un seul affichage dans la liste, même si l'ordinateur possède plusieurs affichages attachés.|
|**Filtrer**|Mots clés qui vous intéressent. Les événements de la partie inférieure du rapport incluent seulement ceux qui correspondent complètement ou partiellement à un mot clé. Vous pouvez spécifier plusieurs mots clés en les séparant par des virgules.|
|**Tri des hiérarchies**|Case à cocher qui indique si les hiérarchies d'événements (définies via des marqueurs utilisateur) sont conservées ou ignorées.|

 La liste des événements dans la partie inférieure du rapport d'utilisation du GPU affiche les détails de chaque événement.

|Colonne|Description|
|------------|-----------------|
|**Nom de l’événement**|Nom de l'événement graphique. Un événement correspond généralement à un événement dans une chronologie de threads de l’UC et à un événement d’une chronologie du GPU.<br /><br /> Des noms d'événements peuvent être « non attribués » si la fonctionnalité d'utilisation du GPU n'a pas pu déterminer le nom d'un événement. Pour plus d'informations, voir la remarque sous ce tableau.|
|**Début UC (ns)**|Heure à laquelle l'événement a débuté sur l'UC en appelant une API Direct3D. Le temps est mesuré en nanosecondes, par rapport au moment où l'application a démarré.|
|**Début GPU (ns)**|Heure à laquelle l'événement a débuté sur le GPU. Le temps est mesuré en nanosecondes, par rapport au moment où l'application a démarré.|
|**Durée GPU (ns)**|Durée d'exécution de l'événement sur le GPU, en nanosecondes.|
|**Nom du processus**|Nom de l'application d'où provient l'événement.|
|**ID de thread**|ID de thread d'où provient l'événement.|

> [!IMPORTANT]
> Si votre GPU ou pilote ne prend pas en charge les fonctionnalités d’instrumentation nécessaires, tous les événements s’affichent comme étant « non attribués ». Veillez à mettre à jour votre GPU/pilote, puis réessayez si vous rencontrez ce problème. Pour plus d’informations, consultez [Prise en charge du matériel et des pilotes](#hwsupport) ci-dessous.

## <a name="gpu-usage-settings"></a>Paramètres d'utilisation du GPU

Vous pouvez configurer l'outil Utilisation du GPU pour reporter la collecte des informations de profilage, au lieu de commencer à collecter les informations dès le démarrage de l'application. Dans la mesure où la taille des informations de profilage peut être significative, cette action est utile quand vous savez que des ralentissements des performances de votre application n’apparaîtront pas avant longtemps.

**Pour différer le profilage à partir du démarrage de l’application :**

1. Dans le menu principal, choisissez **Déboguer**, puis **Performances et diagnostics** (clavier : appuyez sur Alt+F2).

2. Dans le hub Performances et diagnostics, suivez le lien **Paramètres** à côté de l’option **Utilisation du GPU**.

3. Sous **Configuration du profilage GPU**, dans la page de propriétés **Général**, décochez la case **Commencer le profilage au démarrage de l’application** pour reporter le profilage.

   ![Configurer le moment du démarrage de la collecte de données d’utilisation du GPU](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> Le report du profilage n’est actuellement pas pris en charge pour les applications Direct3D 12.

Après l’exécution de votre application dans l’outil Utilisation du GPU, un lien supplémentaire devient disponible dans la partie inférieure de la fenêtre de l’outil Utilisation du GPU. Pour commencer à collecter des informations de profilage, choisissez le lien **Démarrer** dans le message **Commencer à collecter des données détaillées d’utilisation GPU supplémentaires**.

## <a name="hwsupport"></a> Prise en charge du matériel et des pilotes

Le matériel et les pilotes GPU suivants sont pris en charge :

|Fournisseur|Description du GPU|Version de pilote nécessaire|
|------------|---------------------|-----------------------------|
|Intel®|4e génération des processeurs Intel® Core (« Haswell »)<br /><br /> -   Intel® HD Graphics (GT1)<br />-   Intel® HD Graphics 4200 (GT2)<br />-   Intel® HD Graphics 4400 (GT2)<br />-   Intel® HD Graphics 4600 (GT2)<br />-   Intel® HD Graphics P4600 (GT2)<br />-   Intel® HD Graphics P4700 (GT2)<br />-   Intel® HD Graphics 5000 (GT3)<br />-   Intel® Iris™ Graphics 5100 (GT3)<br />-   Intel® Iris™ Pro Graphics 5200 (GT3e)|-- (utilisez les derniers pilotes)|
|AMD®|La plupart, à partir d'AMD Radeon™ HD série 7000 (sauf AMD Radeon™ HD 7350-7670)<br /><br /> GPU AMD Radeon™, GPU AMD FirePro™ et accélérateurs GPU AMD FirePro incluant l'architecture Graphics Core Next (GCN).<br /><br /> Unités de traitement accéléré (APU) AMD® série E et AMD série A incluant l’architecture Graphics Core Next (GCN) - (« Kaveri », « Kabini », « Temash », « Beema », « Mullins »)|14.7 RC3 ou version supérieure|
|NVIDIA®|La plupart, à partir de NVIDIA® GeForce® série 400.<br /><br /> GPU NVIDIA® GeForce®, GPU NVIDIA Quadro® et accélérateurs GPU NVIDIA® Tesla™ incluant l'architecture Fermi™, Kepler™ ou Maxwell™.|343.37 ou version supérieure|

 Les configurations à plusieurs GPU, comme NVIDIA® SLI™ et AMD Crossfire™, ne sont pas prises en charge pour l’instant. Les configurations graphiques hybrides, telles que NVIDIA® Optimus™ et AMD Enduro™, sont prises en charge.

## <a name="see-also"></a>Voir aussi

- [Résoudre les problèmes graphiques complexes liés à votre jeu à l’aide des outils DirectX (vidéo)](https://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)
- [Outil Utilisation du GPU dans Visual Studio (vidéo)](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)
- [Outil Utilisation du GPU dans Visual Studio 2013 Update 4 CTP1 (blog)](https://devblogs.microsoft.com/cppblog/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1/)
- [Utilisation du GPU pour DirectX dans Visual Studio (blog)](https://blogs.msdn.microsoft.com/ianhu/2014/12/16/gpu-usage-for-directx-in-visual-studio/)
- [GPUView](/windows-hardware/drivers/display/using-gpuview)
- [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)