---
title: Utilisation du GPU | Microsoft Docs
ms.date: 11/01/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a738490933c6f2d1cdf89e7e974a268540af991
ms.sourcegitcommit: 14637be49401f56341c93043eab560a4ff6b57f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90074967"
---
# <a name="gpu-usage"></a>Utilisation du GPU

Utilisez l’outil utilisation du GPU dans le profileur de performances pour mieux comprendre l’utilisation du matériel de haut niveau de votre application Direct3D. Elle vous permet de déterminer si les performances de votre application sont liées à l’UC ou au GPU, et d’obtenir des informations sur la façon dont vous pouvez utiliser le matériel de la plateforme de manière plus efficace. L’utilisation du GPU prend en charge les applications qui utilisent Direct3D 12, Direct3D 11 et Direct3D 10. Elle ne prend pas en charge les autres API graphiques, telles que Direct2D ou OpenGL.

Voici à quoi ressemble la fenêtre **rapport d’utilisation du GPU** :

![Capture d’écran du rapport d’utilisation du GPU, avec les chronologies processeur et GPU](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>Configuration requise

Outre la configuration requise pour Graphics Diagnostics, les conditions suivantes sont requises pour l’utilisation de l’outil utilisation du GPU :

- GPU et pilote qui prennent en charge l'instrumentation de minutage nécessaire.

  > [!NOTE]
  > Pour plus d’informations sur le matériel et les pilotes pris en charge, consultez [Prise en charge du matériel et des pilotes](#hwsupport) à la fin de ce document.

Pour plus d’informations sur la configuration requise pour Graphics Diagnostics, consultez [prise](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md)en main.

## <a name="use-the-gpu-usage-tool"></a>Utiliser l’outil utilisation du GPU

Quand vous exécutez votre application dans l’outil utilisation du GPU, Visual Studio crée une session de diagnostic. Cette session présente des informations de haut niveau sur les performances de rendu de votre application et sur l’utilisation du GPU en temps réel.

Pour démarrer l'outil Utilisation du GPU :

1. Dans le menu principal, choisissez **Debug**  >  **performances et diagnostics** du débogage (ou, dans le clavier, appuyez sur Alt + F2).

2. Dans le Hub **performances et diagnostics** , activez la case à cocher en regard de **utilisation du GPU**. Vous pouvez éventuellement cocher les cases en regard des autres outils qui vous intéressent. Vous pouvez exécuter simultanément plusieurs outils de diagnostic et de performances pour obtenir une image plus complète des performances de votre application.

    ![Capture d’écran du profileur de performances, avec l’utilisation de GPU sélectionnée](media/gpuusageselected.png "Utilisation du GPU sélectionnée")

   > [!NOTE]
   > Les outils de performances et de diagnostics ne peuvent pas tous être utilisés en même temps.

3. En bas du Hub **performances et diagnostics** , sélectionnez **Démarrer** pour exécuter votre application sous les outils que vous avez sélectionnés.

Les informations de haut niveau affichées en temps réel incluent le minutage des frames, la fréquence d’images et l’utilisation du GPU. Chacun de ces éléments d’information est graphiquement de manière indépendante, mais ils utilisent tous une échelle de temps commune afin que vous puissiez facilement comprendre les relations.

Les graphiques **temps de trame (MS)** et **images par seconde (FPS)** ont chacun deux lignes horizontales rouges qui affichent les cibles de performances 60 et 30 images par seconde. Dans le graphique Durée de frame, votre application dépasse les performances cibles quand la courbe est en dessous de la ligne, et n’atteint pas la cible quand la courbe est au-dessus de la ligne. Pour le graphique images par seconde, c’est le contraire : votre application dépasse la cible de performance lorsque le graphique est au-dessus de la ligne, et elle n’atteint pas la cible lorsque le graphique est en dessous de la ligne. Vous utilisez ces graphiques principalement pour obtenir une idée générale des performances de votre application et pour identifier les ralentissements que vous pourriez souhaiter examiner. Par exemple, une investigation plus poussée peut être garantie si vous voyez une chute soudaine de la fréquence d’images ou un pic d’utilisation du GPU.

Pendant que votre application s’exécute dans l’outil utilisation du GPU, la session de diagnostic collecte également des informations détaillées sur les événements graphiques qui ont été exécutés sur le GPU. Vous utilisez ces informations pour générer un rapport plus granulaire sur la façon dont votre application utilise le matériel. Dans la mesure où ce rapport prend un certain temps pour générer les résultats à partir des informations collectées, il est disponible uniquement à la fin de la collecte d’informations de la session de diagnostic.

Lorsque vous souhaitez examiner plus attentivement un problème de performances ou d’utilisation, arrêtez la collecte des informations de performances, afin de pouvoir générer le rapport.

Pour générer et afficher le rapport d’utilisation du GPU :

1. Dans la partie inférieure de la fenêtre de session de diagnostic, choisissez le lien **arrêter la collecte** ou sélectionnez **arrêter** dans le coin supérieur gauche.

   ![Capture d’écran de la fenêtre de session de diagnostic](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. Dans la partie supérieure du rapport, sélectionnez une section dans l'un des graphiques qui illustre le problème à examiner. Votre sélection peut atteindre jusqu’à 3 secondes. Les sections plus longues sont tronquées vers le début.

   ![Capture d’écran de la fenêtre de session de diagnostic](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. Pour afficher une chronologie détaillée de votre sélection, dans la partie inférieure du rapport, dans **... Cliquez ici pour afficher les détails de l’utilisation du GPU pour ce** message de plage, sélectionnez **afficher les détails**.

   ![Capture d’écran de la fenêtre de session de diagnostic, avec la plage sélectionnée](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

Cette sélection ouvre un nouveau document avec onglets qui contient le rapport. Le rapport utilisation du GPU vous aide à déterminer quand un événement graphique est démarré sur l’UC, quand il atteint le GPU et la durée nécessaire à l’exécution du GPU. Ces informations peuvent vous aider à identifier les goulots d’étranglement et les opportunités d’augmentation du parallélisme dans votre code.

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>Exporter vers GPUView ou Windows Performance Analyzer

À compter de Visual Studio 2017, vous pouvez ouvrir ces données avec [GPUView](/windows-hardware/drivers/display/using-gpuview) et [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer). Sélectionnez simplement les liens **ouvrir dans GpuView** ou **ouvrir dans WPA** situés dans le coin inférieur droit de la session de diagnostic.

![Capture d’écran de la fenêtre de session de diagnostic, avec les liens mis en surbrillance](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="use-the-gpu-usage-report"></a>Utiliser le rapport d’utilisation du GPU

La partie supérieure du rapport utilisation du GPU affiche les chronologies de l’activité de traitement de l’UC, de l’activité de rendu GPU et de l’activité de copie GPU. Ces chronologies sont divisées par des barres verticales gris clair qui indiquent le Vsync de l’affichage. La fréquence des barres correspond à la fréquence d’actualisation de l’un des affichages (sélectionné à l’aide de la liste déroulante **affichage** ) à partir duquel les données d’utilisation du GPU ont été collectées.

Dans la mesure où l’affichage peut avoir une fréquence de rafraîchissement plus élevée que les performances cibles de votre application, il est possible qu’il n’existe pas de relation 1 à 1 entre le VSync et la fréquence d’images que votre application doit atteindre. Pour atteindre ses objectifs de performances, une application doit effectuer tout le traitement, effectuer le rendu et effectuer un `Present()` appel à la cadence ciblée. Toutefois, le frame rendu ne s’affichera pas jusqu’au prochain Vsync après `Present()` .

La partie inférieure du rapport utilisation du GPU répertorie les événements graphiques qui se sont produits pendant la période du rapport. Lorsque vous sélectionnez un événement, un marqueur apparaît aux événements correspondants dans les chronologies correspondantes. En règle générale, un événement sur un thread d’UC montre l’appel de l’API, tandis qu’un autre événement sur une des chronologies du GPU apparaît quand le GPU a terminé la tâche. De même, lorsque vous sélectionnez un événement dans une chronologie, le rapport met en surbrillance les événements graphiques correspondants dans la partie inférieure du rapport.

Lorsque vous effectuez un zoom arrière des chronologies dans la partie supérieure du rapport, seuls les événements les plus longs sont visibles. Pour afficher les événements qui ont une durée plus petite, effectuez un zoom avant sur les chronologies à l’aide de CTRL + roulette sur votre dispositif de pointage, ou du contrôle de mise à l’échelle dans le coin inférieur gauche du panneau supérieur. Vous pouvez également faire glisser le contenu du panneau de chronologie pour parcourir les événements enregistrés.

Pour vous aider à trouver ce que vous recherchez, filtrez le rapport d’utilisation du GPU en fonction des noms de processus, des ID de thread et du nom de l’événement. En outre, vous pouvez choisir la fréquence d’actualisation de l’affichage qui détermine les lignes de VSync. Vous pouvez trier les événements hiérarchiquement si votre application utilise l’interface [ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) pour regrouper les commandes de rendu.

 Voici plus de détails :

|Contrôle de filtre|Description|
|--------------------|-----------------|
|**Processus**|Nom du processus qui vous intéresse. Tous les processus qui ont utilisé le GPU pendant la session de diagnostic sont inclus dans cette liste déroulante. La couleur associée au processus est la couleur de l’activité du thread dans les chronologies.|
|**Thread**|ID de thread qui vous intéresse. Dans une application multithread, ces informations peuvent vous aider à isoler des threads particuliers qui appartiennent au processus qui vous intéresse. Les événements associés au thread sélectionné sont mis en surbrillance dans chaque chronologie.|
|**Affichage**|Numéro de l’affichage dont la fréquence de rafraîchissement est indiquée. Certains pilotes peuvent être configurés pour présenter plusieurs affichages physiques sous forme d'un affichage virtuel unique, de grande taille. Vous ne verrez peut-être qu'un seul affichage dans la liste, même si l'ordinateur possède plusieurs affichages attachés.|
|**Filter**|Mots clés qui vous intéressent. Les événements dans la partie inférieure du rapport incluent uniquement ceux qui correspondent à un mot clé, entièrement ou partiellement. Vous pouvez spécifier plusieurs mots clés en les séparant par des virgules.|
|**Tri des hiérarchies**|Une case à cocher qui indique si les hiérarchies d’événements, définies via des marqueurs utilisateur, sont conservées ou ignorées.|

La liste des événements dans la partie inférieure du rapport utilisation du GPU affiche les détails de chaque événement.

|Colonne|Description|
|------------|-----------------|
|**Nom de l’événement**|Nom de l'événement graphique. Un événement correspond généralement à un événement dans une chronologie de threads de l’UC et à un événement d’une chronologie du GPU. Les noms d’événements peuvent être *désattributés* si l’utilisation du GPU ne peut pas déterminer le nom d’un événement. Pour plus d’informations, consultez la remarque qui suit ce tableau.|
|**Début UC (ns)**|Heure à laquelle l'événement a débuté sur l'UC en appelant une API Direct3D. Le temps est mesuré en nanosecondes, par rapport au moment où l'application a démarré.|
|**Début GPU (ns)**|Heure à laquelle l'événement a débuté sur le GPU. Le temps est mesuré en nanosecondes, par rapport au moment où l'application a démarré.|
|**Durée GPU (ns)**|Durée, en nanosecondes, nécessaire pour terminer l’événement sur le GPU.|
|**Nom du processus**|Nom de l'application d'où provient l'événement.|
|**ID du thread**|ID de thread d'où provient l'événement.|

> [!IMPORTANT]
> Si votre GPU ou pilote ne prend pas en charge les fonctionnalités d’instrumentation nécessaires, tous les événements s’affichent comme étant non *attributs*. Si vous rencontrez ce problème, mettez à jour votre pilote GPU, puis réessayez. Pour plus d’informations, consultez [prise en charge du matériel et des pilotes](#hwsupport) à la fin de ce document.

## <a name="gpu-usage-settings"></a>Paramètres d'utilisation du GPU

Vous pouvez configurer l'outil Utilisation du GPU pour reporter la collecte des informations de profilage, au lieu de commencer à collecter les informations dès le démarrage de l'application. Dans la mesure où la taille des informations de profilage peut être significative, cette action est utile quand vous savez que des ralentissements des performances de votre application n’apparaîtront pas avant longtemps.

Pour reporter le profilage au démarrage de l'application :

1. Dans le menu principal, choisissez **Debug**  >  **performances et diagnostics** du débogage (ou, dans le clavier, appuyez sur Alt + F2).

2. Dans le Hub **performances et diagnostics** , en regard de **utilisation du GPU**, sélectionnez le lien **paramètres** .

3. Sous **configuration du profilage GPU**, dans la page de propriétés **général** , désactivez la case à cocher **commencer le profilage au démarrage** de l’application pour reporter le profilage.

   ![Capture d’écran des pages de propriétés de l’objet, montrant les options de collection](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> À ce stade, vous ne pouvez pas reporter le profilage pour les applications Direct3D 12.

Après l’exécution de votre application dans l’outil Utilisation du GPU, un lien supplémentaire devient disponible dans la partie inférieure de la fenêtre de l’outil Utilisation du GPU. Pour commencer à collecter des informations de profilage, choisissez le lien **Démarrer** dans le message **Commencer à collecter des données détaillées d’utilisation GPU supplémentaires**.

## <a name="hardware-and-driver-support"></a><a name="hwsupport"></a> Prise en charge du matériel et des pilotes

Le matériel et les pilotes GPU suivants sont pris en charge :

|Fournisseur|Description du GPU|Version du pilote requise|
|------------|---------------------|-----------------------------|
|Intel®|4e génération des processeurs Intel® Core (« Haswell »)<br /><br /> -   Intel® HD Graphics (GT1)<br />-   Intel® HD Graphics 4200 (GT2)<br />-   Intel® HD Graphics 4400 (GT2)<br />-   Intel® HD Graphics 4600 (GT2)<br />-   Intel® HD Graphics P4600 (GT2)<br />-   Intel® HD Graphics P4700 (GT2)<br />-   Intel® HD Graphics 5000 (GT3)<br />-   Intel® Iris™ Graphics 5100 (GT3)<br />-   Intel® Iris™ Pro Graphics 5200 (GT3e)|(utilisez les derniers pilotes)|
|AMD®|La plupart depuis la série AMD Radeon™ HD 7000 (exclut les AMD Radeon™ HD 7350-7670)<br /><br /> Processeur graphique AMD Radeon™, AMD FirePro™ GPU et accélérateurs GPU AMD FirePro avec l’architecture Graphics Core Next (GCN)<br /><br /> Unités de traitement accéléré (APU) AMD® série E et AMD série A incluant l’architecture Graphics Core Next (GCN) - (« Kaveri », « Kabini », « Temash », « Beema », « Mullins »)|14,7 RC3 ou version ultérieure|
|NVIDIA®|La plupart depuis la série NVIDIA® GeForce® 400<br /><br /> NVIDIA® GeForce® GPU, NVIDIA Quadro® GPU et NVIDIA® Tesla™ GPU Accelerators avec Fermi™, Kepler™ ou Maxwell™ architecture|343,37 ou version ultérieure|

 Les configurations à plusieurs GPU, telles que NVIDIA® SLI™ et AMD Crossfire™, ne sont pas prises en charge pour le moment. Les configurations graphiques hybrides, telles que NVIDIA® Optimus™ et AMD enduro™, sont prises en charge.
