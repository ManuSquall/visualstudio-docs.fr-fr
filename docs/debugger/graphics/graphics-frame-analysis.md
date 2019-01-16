---
title: Analyse des frames graphiques | Microsoft Docs
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.frameanalysis
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4aced0df16791e44c7fd8be67ccc22343b1272fa
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154374"
---
# <a name="graphics-frame-analysis"></a>Analyse des frames graphiques
Utilisez l’analyse des frames graphiques dans Visual Studio Graphics Analyzer pour analyser et optimiser les performances de rendu de votre jeu ou application Direct3D.  

## <a name="frame-analysis"></a>Analyse des frames  
 Si l'analyse des frames utilise les mêmes informations que celles capturées dans un fichier journal de graphisme à des fins de diagnostic, elle les utilise en revanche pour résumer les performances de rendu. Les informations de performance ne sont pas enregistrées dans le journal pendant la capture ; elles sont générées ultérieurement pendant l'analyse des frames en chronométrant les événements et en collectant les statiques à mesure que les frames sont lus. Cette approche présente plusieurs avantages par rapport à l'enregistrement des informations de performances pendant la capture :  
  
- L'analyse des frames peut calculer la moyenne des résultats de plusieurs lectures d'un même frame pour s'assurer que le résumé des performances est cohérent du point de vue statistique.  
  
- L'analyse des frames peut générer des informations de performances pour des configurations matérielles et des appareils autres que ceux sur lesquels les informations ont été capturées.  
  
- L’analyse des frames peut générer de nouveaux résumés de performances à partir d’informations capturées antérieurement (par exemple, quand les pilotes GPU sont optimisés ou qu’ils proposent des fonctionnalités de débogage supplémentaires).  
  
  En plus de ces avantages, l'analyse des frames permet aussi de changer la façon dont le frame est affiché pendant la lecture avec la possibilité de présenter des informations sur l'impact potentiel de ces changements sur les performances de rendu d'une application. Vous pouvez vous servir de ces informations pour tester les stratégies d'optimisation potentielles sans avoir à les implémenter, puis capturer et comparer tous les résultats.  
  
  Bien que l'analyse des frames vise essentiellement à vous aider à accéder à de meilleures performances de rendu, elle peut également vous aider à obtenir une meilleure qualité visuelle pour une cible de performances donnée ou à réduire la consommation d'énergie du GPU.  
  
  Pour voir une démonstration de ce que l’analyse des frames peut faire pour votre application, vous pouvez regarder la [Visual Studio Graphics Frame Analysis](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) vidéo sur Channel 9.  
  
## <a name="using-frame-analysis"></a>Utilisation de l'analyse des frames  
 Avant de pouvoir utiliser l'analyse des frames, vous devez d'abord capturer les informations graphiques de votre application pendant qu'elle s'exécute, comme vous le feriez avec un autre outil Graphics Analyzer. Ensuite, dans la fenêtre du document journal de graphisme (.vsglog), choisissez l’onglet **Analyse des frames**.  
  
 ![Sélectionnez l’onglet Analyse des frames](media/pix_frame_analysis_select_tab.png "pix_frame_analysis_select_tab")  
  
 Une fois l'analyse terminée, les résultats s'affichent. La partie supérieure de l'onglet d'analyse des frames affiche la chronologie et le tableau de résumé. La partie inférieure affiche les tableaux contenant les détails. Si des erreurs ou des avertissements ont été générés pendant la lecture, ils sont résumés au-dessus de la chronologie ; de là, vous pouvez suivre les liens pour obtenir des informations supplémentaires sur les erreurs et les avertissements.  
  
### <a name="interpreting-results"></a>Interprétation des résultats  
 De l'interprétation des résultats de chaque variante, vous pouvez tirer des informations utiles sur les performances de rendu et le comportement de votre application. Pour plus d’informations sur les variantes de rendu, consultez [Variantes](#Variants) plus loin dans cet article.  
  
 Certains résultats montrent directement les effets d'une variante sur les performances de rendu :  
  
- Si le filtrage de texture bilinéaire a donné lieu à des gains de performances, l'utilisation de ce mode dans votre application se traduira par les mêmes gains de performances.  
  
- Si la variante Fenêtre d'affichage 1x1 a donné lieu à des gains de performances, la réduction de la taille des cibles de rendu dans votre application améliorera ses performances de rendu.  
  
- Si la variante de compression de texture BC a donné lieu à des gains de performances, l'utilisation de ce mode dans votre application se traduira par les mêmes gains de performances.  
  
- Si la variante MSAAx2 offre des performances proches de la variante MSAAx0, vous pouvez activer MSAAx0 dans votre application pour améliorer sa qualité de rendu sans supporter de coût en matière de performances.  
  
  Les autres résultats peuvent suggérer des incidences plus profondes et plus subtiles pour les performances de votre application :  
  
- Si la variante Fenêtre d'affichage 1x1 donne lieu à des gains de performances très importants, il est probable que votre application consomme un taux de remplissage supérieur à ce qui est disponible. Si les gains de performances apportés par cette variante sont nuls, il est probable que l'application traite trop de sommets.  
  
- Si la variante Format de cible de rendu 16 bpp ne montre pas de gains de performances significatifs, il est probable que votre application consomme trop de bande passante de mémoire.  
  
- Si la variante Dimensions de la texture moitié/un quart montre des gains de performances significatifs, il est probable que vos textures occupent trop de mémoire, consomment trop de bande passante ou n'utilisent pas efficacement le cache de texture. Si cette variante ne montre aucune évolution des performances, vous pouvez probablement utiliser des textures plus grandes et plus détaillées sans supporter de coût en matière de performances.  
  
  Si vous disposez de compteurs matériels, vous pouvez les utiliser pour recueillir des informations très détaillées qui vous renseignerons sur les risques de détérioration des performances de rendu auxquels votre application est exposée. Tous les appareils du niveau de fonctionnalité 9.2 et supérieur prennent en charge les requêtes d’occlusion en profondeur (compteur **Pixels bloqués**) et les horodateurs. Il se peut que d'autres compteurs matériels soient disponibles si le fabricant de GPU les a implémentés, et les a exposés dans son pilote. Vous pouvez utiliser ces compteurs pour confirmer la cause exacte des résultats affichés dans le tableau Résumé (par exemple, vous pouvez déterminer si la superposition est un facteur en examinant le pourcentage de pixels qui ont été bloqués par le test de profondeur).  
  
### <a name="timeline-and-summary-table"></a>Chronologie et tableau Résumé  
 Par défaut, la chronologie et le tableau Résumé sont affichés et les autres sections sont réduites.  
  
#### <a name="timeline"></a>Chronologie  
 La chronologie offre une vue d'ensemble des minutages d'appels de dessin les uns par rapport aux autres. Sachant que le barres les plus longues correspondent aux temps d'appel les plus longs, vous pouvez vous en servir pour repérer rapidement les appels de dessin les plus coûteux du frame. Quand le frame capturé contient un très grand nombre d'appels de dessin, ceux-ci sont combinés en une barre unique dont la longueur représente la somme de ces appels de dessin.  
  
 ![La chronologie indique le dessin&#45;appeler les coûts. ](media/pix_frame_analysis_timeline.png "pix_frame_analysis_timeline")  
  
 Vous pouvez placer le pointeur sur une barre pour déterminer à quel événement d'appel de dessin la barre correspond. Si vous sélectionnez la barre, la liste d'événements se synchronise avec cet événement.  
  
#### <a name="table"></a>Table  
 Le tableau contenant les nombres en dessous de la chronologie présente les performances relatives de chaque variante de rendu pour chaque appel de dessin par rapport au rendu par défaut de votre application. Chaque colonne affiche une variante de rendu différente et chaque ligne représente un appel de dessin différent identifié dans la colonne la plus à gauche ; de là, vous pouvez suivre un lien vers l'événement dans la fenêtre Liste des événements Graphics.  
  
 ![Le tableau récapitulatif montre différents variants. ](media/pix_frame_analysis_summary.png "pix_frame_analysis_summary")  
  
 La deuxième colonne du tableau Résumé en partant de la gauche affiche le temps de rendu du planning de référence de votre application, c’est-à-dire, le temps qu’il faut au rendu par défaut de votre application pour traiter l’appel de dessin. Les autres colonnes présentent les performances relatives de chaque variante de rendu sous la forme d'un pourcentage de la ligne de base, si bien qu'il est plus facile de déterminer si les performances s'améliorent. Les pourcentages supérieurs à 100 % indiquent une durée supérieure à la ligne de base (c'est-à-dire, des performances en baisse), tandis que les pourcentages inférieurs à 100 % ont pris moins de temps (performances en hausse).  
  
 Les valeurs de minutage absolu du planning de référence et le minutage relatif des variantes de rendu sont en réalité des moyennes de plusieurs exécutions (5 par défaut). Cette moyenne est un gage de fiabilité et de cohérence des données de minutage. Vous pouvez placer le pointeur sur chaque cellule du tableau pour examiner les valeurs de minutage minimale, maximale, moyenne et médiane qui ont été observées lors de la génération des résultats de l'appel de dessin et de la variante de rendu en question. Le minutage du planning de référence est aussi indiqué.  
  
#### <a name="hot-draw-calls"></a>Appels de dessin « sensibles »  
 Pour attirer l’attention sur les appels de dessin dont la consommation de temps de rendu global est proportionnellement plus élevée ou qui peuvent être ralentis pour des raisons qui pourraient être évitées, la ligne qui contient ces appels de dessin « sensibles » apparaissent en rouge dès lors que leur propre minutage de planning de référence est plus long d’un écart-type que le minutage de ligne de base moyen de tous les appels de dessin du frame.  
  
 ![Cet appel DrawIndexed possède des variants à chaud et froid. ](media/pix_frame_analysis_hot_calls.png "pix_frame_analysis_hot_calls")  
  
#### <a name="statistical-significance"></a>Signification statistique  
 Pour attirer l'attention sur les variations de rendu les plus pertinentes, l'analyse des frames détermine la signification statistique de chaque variante de rendu et affiche les plus révélatrices en gras. Elle affiche celles qui améliorent les performances en vert et celles qui les diminuent en rouge. Elle affiche les résultats non significatifs du point de vue statistique en caractères normaux.  
  
 ![La pertinence statistique de la variante d’appel de dessin](media/pix_frame_analysis_summary_stats.png "pix_frame_analysis_summary_stats")  
  
 Pour déterminer la pertinence statistique, l’analyse des frames utilise le [test t de Student](http://www.wikipedia.org/wiki/Student%27s_t-test).  
  
### <a name="details-table"></a>Tableau Détails  
 En dessous du tableau Résumé se trouve le tableau Détails, qui est réduit par défaut. Le contenu du tableau Détails dépend de la plateforme matérielle de l'ordinateur de lecture. Pour plus d’informations sur les plateformes matérielles prises en charge, consultez [Prise en charge matérielle](#HardwareSupport).  
  
#### <a name="platforms-that-do-not-support-hardware-counters"></a>Plateformes qui ne prennent pas en charge les compteurs matériels  
 La plupart des plateformes ne prennent pas entièrement en charge les compteurs GPU (c'est le cas notamment de tous les GPU actuellement proposés par Intel, AMD et nVidia). Quand il n'y aucun compteur matériel auprès duquel collecter des données, le tableau Détails s'affiche et contient le minutage absolu moyen de toutes les variantes.  
  
 ![Le tableau de détails et certaines variantes de la lecture. ](media/pix_frame_analysis_details.png "pix_frame_analysis_details")  
  
#### <a name="platforms-that-support-hardware-counters"></a>Plateformes qui prennent en charge les compteurs matériels  
 Pour les plateformes qui prennent en charge les compteurs GPU matériels (par exemple, le SOC T40 SOC et tous les SOC Qualcomm), plusieurs tableaux Détails s'affichent, un pour chaque variante. Chaque compteur matériel disponible fait l'objet d'une collecte pour chaque variante de rendu et est affiché dans son propre tableau Détails.  
  
 ![Compteurs matériels sont affichés lors de la prise en charge. ](media/pix_frame.png "pix_frame")  
  
 Les informations de compteur matériel fournissent une vue très détaillée du comportement spécifique de la plateforme matérielle pour chaque appel de dessin, ce qui peut vous aider à identifier très précisément la cause des goulots d'étranglement qui nuisent aux performances.  
  
> [!NOTE]
>  Les compteurs pris en charge par les plateformes sont variables ; aucune norme n'existe dans ce domaine. Les compteurs et ce qu'ils représentent sont déterminés uniquement par le fabricant de chaque GPU.  
  
### <a name="marker-regions-and-events"></a>Régions de marqueur et événements  
 L'analyse des frames prend en charge les marqueurs d'événements et les groupes d'événements définis par l'utilisateur. Ils sont affichés dans le tableau Résumé et dans les tableaux de détails.  
  
 Vous pouvez utiliser les API ID3DUserDefinedAnnotation ou la famille d'API existante D3DPERF_ pour créer des marqueurs et des groupes. Quand vous utilisez la famille d'API D3DPERF_, vous pouvez assigner à chaque marqueur et groupe une couleur que l'analyse des frames affiche sous forme de bande colorée dans les lignes qui contiennent le marqueur d'événement ou les marqueurs de début/fin du groupe d'événements et leur contenu. Cette fonctionnalité peut vous aider à repérer rapidement les événements de rendu ou les groupes d’événements importants.  
  
### <a name="warnings-and-errors"></a>Avertissements et erreurs  
 L'analyse des frames se termine parfois avec des avertissements et des erreurs, qui sont résumés au-dessus de la chronologie et détaillés au bas de l'onglet Analyse des frames.  
  
 En général, les avertissements et les erreurs sont communiqués à titre d'information uniquement et ne demandent aucune intervention.  
  
 Les avertissements indiquent le plus souvent un défaut de prise en charge matérielle mais qui peut être contourné, une impossibilité de collecter des données de compteurs matériels ou le manque de fiabilité possible de certaines données de performance (par exemple, quand elles sont faussées par une solution de contournement).  
  
 Les erreurs indiquent généralement la présence de bogues au niveau d'un pilote, de l'implémentation de l'analyse des frames, d'un défaut de prise en charge matérielle qui ne peut pas être contourné, ou encore que l'application tente quelque chose qui n'est pas pris en charge par la lecture.  
  
### <a name="retries"></a>Nouvelles tentatives  
 Si le GPU connaît une transition de l'état d'alimentation pendant l'analyse des frames, l'analyse affectée doit être retentée, car la vitesse d'horloge du GPU a changé, ce qui a eu pour effet d'invalider les résultats du minutage relatif.  
  
 L'analyse des frames limite le nombre de nouvelles tentatives à 10. Si votre plateforme a recours à une gestion de l'alimentation agressive ou au « clock gating », cela peut entraîner l'échec de l'analyse des frames et le signalement d'une erreur pour dépassement de la limite de nouvelles tentatives. Vous pouvez atténuer ce problème en réinitialisant la gestion de l'alimentation de votre plateforme et en choisissant une vitesse d'horloge moins agressive, si la plateforme le permet.  
  
##  <a name="HardwareSupport"></a> Prise en charge matérielle  
  
### <a name="timestamps-and-occlusion-queries"></a>Horodateurs et requêtes d'occlusion  
 Les horodateurs sont pris en charge sur toutes les plateformes prenant en charge l'analyse des frames. Les requêtes d'occlusion en profondeur (nécessaires au compteur Pixels bloqués) sont prises en charge sur les plateformes qui prennent en charge le niveau de fonctionnalité 9.2 ou supérieur.  
  
> [!NOTE]
>  Bien que les horodateurs soient pris en charge sur toutes les plateformes qui gèrent l'analyse des frames, la précision et la cohérence des horodateurs varient d'une plateforme à l'autre.  
  
### <a name="gpu-counters"></a>Compteurs GPU  
 La prise en charge des compteurs matériels GPU varie en fonction du matériel.  
  
 Comme aucun des GPU d'ordinateur actuellement proposés par Intel, AMD ou nVidia n'assure une prise en charge sûre des compteurs matériels GPU, l'analyse des frames ne collecte pas de données des compteurs de ces matériels. Toutefois, l’analyse des frames collecte des compteurs matériels à partir de la GPU suivant, qui les prend en charge fiable :  
  
- nVidia T40 (Tegra4)
  
  Aucune autre plateforme prenant en charge l'analyse des frames n'assure de collecte auprès des compteurs matériels GPU.  
  
> [!NOTE]
>  Dans la mesure où les compteurs matériels GPU sont des ressources matérielles, plusieurs passages peuvent être nécessaires pour collecter l'ensemble des compteurs matériels pour chaque variante de rendu. Ainsi, l'ordre dans lequel les compteurs GPU sont collectés n'est pas spécifié.  
  
## <a name="unsupported-scenarios"></a>Scénarios non pris en charge  
 Certains modes d'utilisation de l'analyse des frames ne sont pas pris en charge ou sont simplement déconseillés.  
  
### <a name="playback-of-high-feature-level-captures-on-down-level-devices"></a>Lecture de captures d’un niveau de fonctionnalité élevé sur des appareils moins élaborés  
 Dans Graphics Analyzer, quand vous lisez un fichier journal de graphisme qui utilise un niveau de fonctionnalité trop élevé pour l'ordinateur de lecture, il repasse automatiquement à WARP. Dans l'analyse des frames, il ne repasse pas explicitement à WARP et une erreur est générée (si WARP est utile pour examiner la justesse de votre application Direct3D, il ne l'est pas pour examiner ses performances).  
  
> [!NOTE]
>  Bien qu’il soit important de ne pas perdre de vue les problèmes de niveau de fonctionnalité, vous pouvez capturer et lire les fichiers journaux de graphisme sur des configurations matérielles et des appareils différents. Le journal de graphisme peut être lu tant que le fichier journal ne contiennent des API ou utiliser des niveaux de fonctionnalité qui ne sont pas pris en charge sur l’ordinateur de lecture.  
  
### <a name="direct3d-10-and-lower"></a>Direct3D version 10 et inférieure  
 Si votre application appelle l'API Direct3D 10, l'analyse des frames ne reconnaîtra ni ne profilera ces appels, même s'ils sont reconnus et utilisés par d'autres outils Graphics Analyzer.
  
> [!NOTE]
>  Cela vaut uniquement pour les appels d’API Direct3D que vous utilisez, et non aux niveaux de fonctionnalité.

### <a name="warp"></a>WARP  
 L'analyse des frames vise à profiler et à améliorer les performances de rendu sur du vrai matériel. Analyse des frames en cours d’exécution sur des appareils WARP n’est pas interdite, mais il est généralement pas payant d’insister car l’exécution sur une UC haut de gamme de WARP est plus lente que même les moins performant des GPU actuels, et les performances de WARP peuvent varier considérablement en fonction de l’UC Il s’exécute sur.  
  
##  <a name="Variants"></a> Variantes  
 Chaque modification apportée par l’analyse des frames au mode d’affichage d’un frame en cours de lecture est appelée *variante*. Les variantes examinées par l‘analyse des frames correspondent à des modifications courantes et relativement simples que vous pourriez apporter pour améliorer les performance de rendu ou la qualité visuelle de votre application (par exemple, en réduisant la taille des textures, en utilisant la compression de texture ou en autorisant différents types d‘anticrénelage). Les variantes substituent le contexte et les paramètres de rendu habituels de votre application. Voici un résumé :  
  
|Variante|Description|  
|-------------|-----------------|  
|**Taille fenêtre d’affichage 1x1**|Réduit les dimensions de la fenêtre d'affichage sur toutes les cibles de rendu à 1x1 pixels.<br /><br /> Pour plus d’informations, consultez [Variante de taille Viewport 1x1](1x1-viewport-size-variant.md)|  
|**MSAA 0x**|Désactive l‘anticrénelage MSSA (Multi-Sample Anti-Aliasing) sur toutes les cibles de rendu.<br /><br /> Pour plus d’informations, consultez [Variantes MSAA 0x/2x/4x](0x-2x-4x-msaa-variants.md)|  
|**MSAA 2x**|Active l‘anticrénelage MSSA (Multi-Sample Anti-Aliasing) 2x sur toutes les cibles de rendu.<br /><br /> Pour plus d’informations, consultez [Variantes MSAA 0x/2x/4x](0x-2x-4x-msaa-variants.md)|  
|**MSAA 4x**|Active l‘anticrénelage MSSA (Multi-Sample Anti-Aliasing) 4x sur toutes les cibles de rendu.<br /><br /> Pour plus d’informations, consultez [Variantes MSAA 0x/2x/4x](0x-2x-4x-msaa-variants.md)|  
|**Filtrage de texture de point**|Définit le mode de filtrage `DXD11_FILTER_MIN_MAG_MIP_POINT` (filtrage de texture de point) pour tous les échantillons de texture appropriés.<br /><br /> Pour plus d’informations, consultez [Point, bilinéaire, trilinéaire et ANISOTROPIQUE variantes de filtrage de Texture](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtrage de texture bilinéaire**|Définit le mode de filtrage `DXD11_FILTER_MIN_MAG_LINEAR_MIP_POINT` (filtrage de texture bilinéaire) pour tous les échantillons de texture appropriés.<br /><br /> Pour plus d’informations, consultez [Point, bilinéaire, trilinéaire et ANISOTROPIQUE variantes de filtrage de Texture](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtrage de texture trilinéaire**|Définit le mode de filtrage `DXD11_FILTER_MIN_MAG_MIP_LINEAR` (filtrage de texture trilinéaire) pour tous les échantillons de texture appropriés.<br /><br /> Pour plus d’informations, consultez [Point, bilinéaire, trilinéaire et ANISOTROPIQUE variantes de filtrage de Texture](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtrage de texture anisotropique**|Définit le mode de filtrage `DXD11_FILTER_ANISOTROPIC` et affecte à `MaxAnisotropy` la valeur `16` (filtrage de texture anisotropique 16x) pour tous les échantillons de texture appropriés.<br /><br /> Pour plus d’informations, consultez [Point, bilinéaire, trilinéaire et ANISOTROPIQUE variantes de filtrage de Texture](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Format de cible de rendu 16 bpp**|Définit le format de pixel `DXGI_FORMAT_B5G6R5_UNORM` (format 16 bpp, 565) pour toutes les cibles de rendu et tous les mémoires tampons d'arrière-plan.<br /><br /> Pour plus d’informations, consultez [Variante de format cible de rendu 16 bpp](16bpp-render-target-format-variant.md)|  
|**Génération mipmap**|Active les mipmaps sur toutes les textures qui ne sont pas des cibles de rendu.<br /><br /> Pour plus d’informations, consultez [Variante de génération mipmap](mip-map-generation-variant.md).|  
|**Dimensions de texture moitié**|Réduit les dimensions de toutes les textures qui ne sont pas des cibles de rendu à la moitié de leur taille d'origine dans chaque dimension. Par exemple, une texture de 256 x 128 est réduite à 128 x 64 texels.<br /><br /> Pour plus d’informations, consultez [Variante de dimensions de la texture moitié/un quart](half-quarter-texture-dimensions-variant.md).|  
|**Dimensions de texture un quart**|Réduit les dimensions de toutes les textures qui ne sont pas des cibles de rendu à un quart de leur taille d'origine dans chaque dimension. Par exemple, une texture de 256 x 128 est réduite à 64 x 32 texels.<br /><br /> Pour plus d’informations, consultez [Variante de dimensions de la texture moitié/un quart](half-quarter-texture-dimensions-variant.md).|  
|**Compression de texture BC**|Active la compression de bloc sur toutes les textures ayant une variante de format de pixel B8G8R8X8, B8G8R8A8 ou R8G8B8A8. Les variantes de format B8G8R8X8 sont compressées à l'aide de BC1 ; les variantes de format B8G8R8A8 et R8G8B8A8 sont compressées à l'aide de BC3.<br /><br /> Pour plus d’informations, consultez [Variante de compression de texture BC](bc-texture-compression-variant.md).|  
  
 Le résultat pour la plupart des variantes est normatif : « Réduisant de moitié la taille de texture est 25 % plus rapide » ou « Activation de 2 x MSAA est uniquement de 2 % ». Les autres variantes peuvent nécessiter une interprétation. Par exemple, si la variante qui a fait passer les dimensions de la fenêtre d'affichage à 1x1 donne lieu à un gain de performances important, cela peut indiquer que le rendu est bloqué par un faible taux de remplissage ; en revanche, s'il n'y a pas de changement significatif sur le plan des performances, cela peut indiquer que le rendu est bloqué par le traitement des sommets.