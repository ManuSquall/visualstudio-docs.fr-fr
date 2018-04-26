---
title: 'Le Concepteur de flux de travail - Comment : utiliser l’arborescence de Navigation'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 92f3e35d4182297601741bd603aa3c5a17e54d67
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-breadcrumb-navigation"></a>Procédure : utiliser l'exploration à l'aide de la barre de navigation

Il existe trois méthodes principales pour modifier l’ensemble des activités qui s’affichent dans le Concepteur de flux de travail Windows :

1.  Double-cliquez pour descendre dans la hiérarchie et accéder à une activité enfant.

2.  Cliquez sur un bouton de la barre de navigation pour accéder à une activité ancêtre.

3.  Développez ou réduisez les activités sur place.

## <a name="using-breadcrumb-navigation"></a>Utilisation de l'exploration à l'aide de la barre de navigation

1.  Double-cliquez sur une activité du Concepteur de flux de travail pour modifier l’activité racine à l’activité sélectionnée. L’activité sur laquelle vous avez cliqué est alors entièrement développée à la racine et ses ancêtres sont affichés dans la barre de navigation. Cette procédure est parfois appelée exploration avant ou arrière d'une activité.

2.  Pour accéder à un ancêtre de l'activité racine actuelle, cliquez sur l'activité dans la barre de navigation.

## <a name="expanding-or-collapsing-an-activity-in-place"></a>Développement ou réduction d'une activité sur place

1.  Cliquer sur les chevrons sur une activité se développe ou réduit l'activité en place.

2.  Lorsque l'état de développement est modifié en cliquant sur le bouton, le nouvel état de développement est enregistré en XAML.

    > [!WARNING]
    > Toutes les activités ne peuvent pas être développées sur place. Il existe deux cas pour lesquels il est impossible de développer une activité sur place : soit le parent de l’activité n’autorise pas ses enfants à être développés sur place, (par exemple, les activités d’un organigramme ne peuvent pas être développées sur place), soit le concepteur d’activités lui-même ne peut pas être développé sur place. Bien qu’aucun des concepteurs d’activités incluses dans le Concepteur de flux de travail ont le comportement de ce dernier, certaines activités personnalisées peuvent présenter ce comportement.

## <a name="expanding-all-or-collapsing-all-activities"></a>Développement ou réduction de toutes les activités

1.  Utilisez le **développer tout** et **réduire tout** boutons dans l’interface utilisateur pour développer ou réduire toutes les activités sous la racine de la barre de navigation actuelle. Notez que Développer tout et Réduire tout sont des états globaux. Cela signifie que lorsque vous modifiez l’activité racine à l’aide de la navigation hiérarchique, le développer tout ou réduisez tous les États persiste jusqu'à ce que vous cliquez sur **restaurer**.

2.  Une fois que vous avez appliqué un développer tout ou réduisez tous les États, vous pouvez cliquer sur le **restaurer** bouton qui s’affiche pour revenir à l’état précédemment appliqué à chaque activité.

    > [!WARNING]
    > Si une activité, tels que <xref:System.Activities.Statements.Flowchart>, a choisi de développement en place, les fonctionnalités associées le **développer tout** et **réduire tout** boutons sont désactivé sur le **organigramme**  concepteur. Pour plus d’informations sur la **organigramme** concepteur, voir la [organigramme](../workflow-designer/flowchart-activity-designer.md) rubrique.

    > [!WARNING]
    > Développer tout a également un effet spécial sur **commutateur** et **TryCatch** concepteurs d’activités. Lorsque vous cliquez sur **développer tout**, tous les switch cases et tous les blocs try/catch/finally sont affichés. En cliquant sur **restaurer** ou **réduire tout** ces concepteurs retrouvent leur état par défaut, à partir de laquelle vous pouvez cliquer sur un cas/bloc individuel pour afficher son contenu.