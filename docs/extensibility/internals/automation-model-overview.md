---
title: Vue d’ensemble du modèle Automation | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b940677c370106ebdcc63c7984d553003251e8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710009"
---
# <a name="automation-model-overview"></a>Vue d’ensemble du modèle Automation
Le modèle Automation se compose d’un ensemble d’objets sur lesquels vous pouvez écrire un complément ou une extension Visual Studio. Un complément est une application qui peut manipuler l’environnement Visual Studio et automatiser les tâches courantes. Une extension Visual Studio peut créer des composants Visual Studio personnalisés ou ajouter des fonctionnalités de composants standard tels que l’éditeur de texte.

## <a name="objects-in-the-automation-model"></a>Objets dans le modèle Automation
 Le modèle Automation est constitué de groupes d’objets connexes qui contrôlent les principales facettes de l’environnement commun. Le diagramme suivant illustre l’ensemble complet d’objets Visual Studio qui composent le modèle Automation.

 ![Graphique d’objets Automation Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Pour plus d’informations, consultez [étendre l’environnement Visual Studio](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).

 L’environnement fournit un modèle pour différents domaines fonctionnels. Par exemple, il existe un modèle de code pour les différents éléments que vous pouvez trouver dans le code. Il existe un modèle de document pour différents éléments de document. Une zone, la zone de projet, revêt un intérêt particulier pour les fournisseurs VSPackage. Vous souhaiterez probablement que vos nouveaux types de projets contribuent au modèle Automation à peu près de la même façon que [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuent au modèle Automation. Ce processus est décrit dans [fournir une automatisation pour les VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).

 Emplacements où vous pouvez envisager d’étendre le modèle Automation de l’environnement :

- Project

- Document

- Code

- Build

Pour plus d’informations sur l’automatisation, consultez [Automation et extensibilité pour Visual Studio](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015). Ce document et les documents auxquels il fournit des liens vous aident à prendre des décisions sur la façon dont vous devez fournir l’automatisation pour votre VSPackage.

## <a name="see-also"></a>Voir aussi
- [Comment : créer un complément](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
