---
title: Liste des événements graphiques (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5c4e8f39ff77779985536e53d98ddc2785b109b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302125"
---
# <a name="graphics-event-list"></a>Liste des événements Graphics
La liste des événements Graphics dans Visual Studio Graphics Analyzer vous permet d'explorer les événements Direct3D enregistrés durant le rendu d'un frame de votre jeu ou application.

 Voici la liste des événements :

 ![Liste des événements ayant « Index » dans leur nom.](media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")

## <a name="using-the-event-list"></a>Utilisation de la liste des événements
 Quand vous sélectionnez un événement dans la liste des événements, cela se reflète aussitôt dans les informations affichées par les autres outils Graphics Analysis. En utilisant la liste des événements avec ces autres outils, vous pouvez examiner un problème de rendu en détail pour en identifier la cause. Pour en savoir plus sur la façon de résoudre les problèmes de rendu en combinant la liste des événements aux autres outils Graphics Analysis, consultez [Exemples](graphics-diagnostics-examples.md).

 Il est important de savoir utiliser efficacement les fonctionnalités de la liste des événements pour gérer les frames complexes, qui peuvent contenir plusieurs milliers d’événements. Pour utiliser la liste des événements de manière efficace, choisissez l'affichage qui vous convient le mieux, utilisez la fonction de recherche pour filtrer la liste des événements, suivez les liens pour en savoir plus sur les objets Direct3D associés à un événement, puis utilisez les boutons fléchés pour parcourir rapidement les appels de dessin.

### <a name="color-coded-events-in-direct3d-12"></a>Événements à code de couleurs dans Direct3D 12
 Direct3D 12 expose plusieurs files d'attente qui correspondent à différentes fonctionnalités matérielles. Pour faciliter l'identification de la file d'attente associée à un événement graphique particulier dans Direct3D 12, les événements apparaissent dans la liste des événements sous forme d'événements à code de couleurs en fonction de leur file d'attente quand vous travaillez sur une capture d'une application Direct3D 12.

|File d'attente Direct3D 12|Couleur|
|-----------------------|-----------|
|File d'attente de rendu|Vert|
|File d'attente de calcul|Jaune|
|File d'attente de copie|Orange|

 Dans la mesure où Direct3D 11 n'expose pas plusieurs files d'attente, les événements ne sont pas affichés sous forme d'événements à code de couleurs dans la liste des événements quand vous travaillez sur une capture d'une application Direct3D 11.

### <a name="event-list-views"></a>Affichages de la liste des événements
 La liste des événements propose deux affichages différents qui organisent les événements graphiques de différentes manières pour mieux prendre en compte votre flux de travail et vos préférences. La première vue est la *vue de travail GPU* qui organise des événements et leur état associé hiérarchiquement. Le deuxième est l' *affichage Chronologie* qui organise les événements par ordre chronologique sous forme de liste plate.

 La vue **GPU Work** Affiche les événements capturés et leur état dans une hiérarchie. Le niveau supérieur de la hiérarchie est constituée d'événements tels que des appels de dessin, des effacements, des présences et ceux en rapport avec les affichages. Dans la liste des événements, vous pouvez développer les appels de dessin pour afficher l'état de l'appareil au moment où l'appel de dessin a été émis. Vous pouvez même développer chaque type d'état pour afficher les événements qui ont défini leur valeur. À ce niveau, vous pouvez aussi déterminer si un état particulier a été défini dans un frame précédent ou s'il a été défini plusieurs fois depuis le dernier appel de dessin.

 La **vue Timeline** affiche chaque événement capturé dans l’ordre chronologique. Ce mode d'organisation de la liste des événements est le même que dans les versions précédentes de Visual Studio.

##### <a name="to-change-the-event-list-view-mode"></a>Pour modifier le mode d'affichage de la liste des événements

- Dans la fenêtre **Graphics Event List,** au-dessus de la liste des événements, localiser le dropdown **View** et choisir soit la vue **Timeline** ou la vue **GPU Work.**

### <a name="filtering-events"></a>Filtrage des événements
 Vous pouvez utiliser la zone Rechercher (située dans l'angle supérieur droit de la fenêtre **Liste des événements Graphics** ) pour filtrer la liste des événements et afficher uniquement ceux dont le nom contient les mots clés spécifiés. Vous pouvez spécifier des mots clés uniques comme `Vertex`(comme dans l’illustration précédente) ou des mots clés multiples en utilisant une liste délimitée par des points-virgules, comme `Draw;Primitive`(qui correspond aux événements dont le nom contient `Draw` ou `Primitive` ). Comme les recherches respectent les espaces (par exemple `VSSet``VS Set` sont des recherches différentes), spécifiez vos recherches avec soin.

### <a name="moving-between-draw-calls"></a>Exploration des appels de dessin
 L'examen des appels de dessin ( `Draw` ) étant particulièrement important, vous pouvez utiliser les boutons **Accéder à l'appel de dessin suivant** et **Accéder à l'appel de dessin précédent** (situés dans l'angle supérieur gauche de la fenêtre **Liste des événements Graphics** ) pour rechercher et parcourir rapidement les appels de dessin.

### <a name="links-to-graphics-objects"></a>Liens vers les objets graphiques
 Pour comprendre certains événements graphiques, il peut être nécessaire d'obtenir des informations supplémentaires sur l'état actuel de Direct3D ou sur les objets Direct3D référencés par l'événement. Bon nombre d'événements proposent des liens que vous pouvez suivre pour accéder à des informations supplémentaires.

## <a name="kinds-of-events-and-event-markers"></a>Types d'événements et marqueurs d'événements
 Les événements affichés dans la liste des événements sont organisés en quatre catégories : événements généraux, événements de dessin, groupes d'événements définis par l'utilisateur et marqueurs d'événements définis par l'utilisateur. À l'exception des événements généraux, chaque événement est associé à une icône qui indique sa catégorie d'appartenance.

|Icône|Description de l'événement|
|----------|-----------------------|
|(pas d'icône)|Événement général<br /> Tout événement autre qu'un événement non défini par l'utilisateur, un groupe d'événements défini par l'utilisateur ou un événement de dessin.|
|![Icône d'événement de dessin](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|Événement de dessin<br /> Marque un événement de dessin qui s'est produit pendant le frame capturé.|
|![L’utilisateur&#45;icône définie du marqueur d’événements](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Groupe d'événements définis par l'utilisateur<br /> Événements liés au groupe, tels que définis par l'application.|
|![L’utilisateur&#45;icône définie du marqueur d’événements](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Marqueur d'événement défini par l'utilisateur<br /> Marque un emplacement spécifique, tel que défini par l'application.|

## <a name="marking-user-defined-events-in-your-app"></a>Marquage des événements définis par l'utilisateur dans votre application
 Les événements définis par l'utilisateur sont propres à votre application. Vous pouvez vous en servir pour établir une corrélation entre les événements importants qui se produisent dans votre application et les événements figurant dans la liste des événements Graphics. Par exemple, vous pouvez créer des groupes d'événements définis par l'utilisateur pour organiser les événements associés (par exemple, ceux qui affichent votre interface utilisateur) sous forme de groupes ou de hiérarchies afin de faciliter la navigation dans la liste des événements. De même, vous pouvez créer des marqueurs quand certains types d'objets sont dessinés afin de trouver facilement les événements graphiques correspondants dans la liste des événements.

 Pour créer des groupes et des marqueurs dans votre application, vous devez utiliser les mêmes API Direct3D que celles utilisées par les autres outils de débogage Direct3D. Ces API varient parfois entre les versions de Direct3D, mais la fonctionnalité de base est la même.

### <a name="user-defined-events-in-direct3d-12"></a>Événements définis par l'utilisateur dans Direct3D 12
 Pour créer des groupes et des marqueurs dans Direct3D 12, utilisez les API décrites dans cette section. Le tableau ci-dessous récapitule les API que vous pouvez utiliser selon que vous marquez les événements dans une file d'attente de commandes ou dans une liste de commandes.

|Description de l'API|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|
|---------------------| - | - |
|Vérifier la disponibilité des événements définis par l'utilisateur|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|
|Commencer un groupe d'événements|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-beginevent)|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-beginevent)|
|Terminer un groupe d'événements|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-endevent)|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-endevent)|
|Créer un marqueur d'événement|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-setmarker)|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-setmarker)|

### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Événements définis par l'utilisateur dans Direct3D 11 et les versions antérieures
 Pour créer des groupes et des marqueurs dans Direct3D 11 ou les versions antérieures, utilisez les API décrites dans cette section. Le tableau ci-dessous récapitule les API que vous pouvez utiliser pour les différentes versions de Direct3D 11, ainsi que les versions antérieures de Direct3D.

|Description de l'API|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](/windows/win32/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) (Direct3D 11.1)|Famille d’API D3DPerf_ (Direct3D 11.0 et antérieur)|
|---------------------| - | - | - |
|Commencer un groupe d'événements|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|
|Terminer un groupe d'événements|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|
|Créer un marqueur d'événement|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|

 Vous pouvez utiliser n'importe laquelle de ces API à condition qu'elle soit prise en charge par votre version de Direct3D (par exemple, si vous visez l'API Direct3D 11.1, vous pouvez utiliser `SetMarker` ou `D3DPerf_SetMarker` pour créer un marqueur d'événement, mais pas `SetMarkerInt` , car elle n'est disponible que dans Direct3D 11.2). Vous pouvez même combiner dans une même application celles qui prennent en charge différentes versions de Direct3D.

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## <a name="resource-history"></a>Historique des ressources
Visual Studio 2017 et plus contiennent la fenêtre **d’histoire des ressources.**  La sélection de ![l’icône](media/gfx_watch.png) de montre à côté d’une entrée dans la fenêtre De la **liste d’événements** fera ressortir la fenêtre **d’historique des ressources** indiquée ci-dessous :

![Historique des ressources](media/gfx_diag_resource_history.png)

Cette fenêtre vous permet de visualiser l’historique de l’élément sélectionné dans la liste des événements.  Le dropdown en haut peut être utilisé pour sélectionner d’autres éléments pour afficher l’historique de.  La moitié supérieure de la fenêtre contient les **événements d’installation de cadre**.  Ce sont les événements qui entrent dans la catégorie de type *Créer* et sont des appels qui sont généralement initialiser et créer la ressource.  La moitié inférieure de la fenêtre contient la section **Frame Events.**  Ce sont les événements normaux de lecture et d’écriture qui se produisent pendant l’utilisation de la ressource.

| Colonne | Description |
|-----------| - |
| **Type** | Affiche le type d’entrée, généralement *créer*, *Lire* et *écrire*. |
| **View** | Montre une vignette de la ressource à ce moment-là dans le temps.  Double-cliquez sur la vignette pour ouvrir une vue de détails de la ressource à ce moment-là. |
| **Événement** | Affiche l’appel de méthode qui s’est produit qui a généré l’événement.  Toute historique supplémentaire sur des éléments individuels peut ![être](media/gfx_watch.png) visualisée en sélectionnant l’icône de montre de montre sur la ligne appropriée.  En outre, tout élément qui est `m_commandList` dessiné dans le texte bleu, comme dans la capture d’écran ci-dessus, peut être sélectionné pour plus de détails. |

<!-- /VERSIONLESS -->

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : objets manquants en raison de l'état du périphérique](walkthrough-missing-objects-due-to-device-state.md)