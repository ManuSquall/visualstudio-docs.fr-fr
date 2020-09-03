---
title: 'Comment : utiliser la navigation de navigation | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c01e48e6aa34513e57b373150c605cb0a7f5b18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659156"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Procédure : utiliser l'exploration à l'aide de la barre de navigation
Il existe trois méthodes principales pour modifier l'ensemble des activités affichées dans [!INCLUDE[wfd1](../includes/wfd1-md.md)] :

1. Double-cliquez pour descendre dans la hiérarchie et accéder à une activité enfant.

2. Cliquez sur un bouton de la barre de navigation pour accéder à une activité ancêtre.

3. Développez ou réduisez les activités sur place.

### <a name="using-breadcrumb-navigation"></a>Utilisation de l'exploration à l'aide de la barre de navigation

1. Double-cliquez sur une activité de [!INCLUDE[wfd2](../includes/wfd2-md.md)] pour qu'elle remplace l'activité racine. L’activité sur laquelle vous avez cliqué est alors entièrement développée à la racine et ses ancêtres sont affichés dans la barre de navigation. Cette procédure est parfois appelée exploration avant ou arrière d'une activité.

2. Pour accéder à un ancêtre de l'activité racine actuelle, cliquez sur l'activité dans la barre de navigation.

### <a name="expanding-or-collapsing-an-activity-in-place"></a>Développement ou réduction d'une activité sur place

1. Cliquer sur les chevrons sur une activité se développe ou réduit l’activité en place.

2. Lorsque l'état de développement est modifié en cliquant sur le bouton, le nouvel état de développement est enregistré en XAML.

    > [!WARNING]
    > Toutes les activités ne peuvent pas être développées sur place. Il existe deux cas pour lesquels il est impossible de développer une activité sur place : soit le parent de l’activité n’autorise pas ses enfants à être développés sur place, (par exemple, les activités d’un organigramme ne peuvent pas être développées sur place), soit le concepteur d’activités lui-même ne peut pas être développé sur place. Bien que ce ne soit pas le cas des concepteurs d'activités inclus dans [!INCLUDE[wfd2](../includes/wfd2-md.md)], certaines activités personnalisées peuvent présenter ce comportement.

### <a name="expanding-all-or-collapsing-all-activities"></a>Développement ou réduction de toutes les activités

1. Utilisez les boutons **développer tout** et **réduire tout** dans l’interface utilisateur pour développer ou réduire toutes les activités sous la racine de navigation actuelle. Notez que Développer tout et Réduire tout sont des états globaux. Cela signifie que lorsque vous modifiez l’activité racine à l’aide de la navigation de navigation, l’état développer tout ou réduire tout est conservé jusqu’à ce que vous cliquiez sur **restaurer**.

2. Une fois que vous avez appliqué un état développer tout ou réduire tout, vous pouvez cliquer sur le bouton **restaurer** qui s’affiche pour revenir à l’état précédemment appliqué à chaque activité.

    > [!WARNING]
    > Si une activité, telle que <xref:System.Activities.Statements.Flowchart> , a désactivé l’expansion sur place, les fonctionnalités associées aux boutons **développer tout** et **réduire tout** sont désactivées sur le concepteur d' **organigrammes** . [!INCLUDE[crabout](../includes/crabout-md.md)] le concepteur d' **organigrammes** , consultez la rubrique [organigramme](../workflow-designer/flowchart-activity-designer.md) .

    > [!WARNING]
    > L’option développer tout a également un effet spécial dans les concepteurs d’activités **switch** et **TryCatch** . Quand vous cliquez sur **développer tout**, tous les cas de basculement et tous les blocs try/catch/finally s’affichent. Si vous cliquez sur **restaurer** ou **réduire tout** , ces concepteurs sont rétablis à leur état par défaut, à partir duquel vous pouvez cliquer sur un bloc/cas individuel pour afficher son contenu.