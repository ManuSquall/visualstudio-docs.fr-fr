---
title: Aperçu du modèle d’automatisation (en anglais) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710009"
---
# <a name="automation-model-overview"></a>Aperçu du modèle d’automatisation
Le modèle d’automatisation se compose d’un ensemble d’objets contre lesquels vous pouvez écrire un add-in ou une extension Visual Studio. Un add-in est une application qui peut manipuler l’environnement Visual Studio et automatiser les tâches courantes. Une extension Visual Studio peut créer des composants Visual Studio personnalisés ou ajouter à la fonctionnalité de composants standard tels que l’éditeur de texte.

## <a name="objects-in-the-automation-model"></a>Objets dans le modèle d’automatisation
 Le modèle d’automatisation se compose de groupes d’objets connexes qui contrôlent les principales facettes de l’environnement commun. Le diagramme suivant montre l’ensemble étendu d’objets Visual Studio qui composent le modèle d’automatisation.

 ![Graphique d’objets d’automatisation visual des studios](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Pour plus d’informations, voir [Extend the Visual Studio environnement](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).

 L’environnement fournit un modèle pour différents domaines fonctionnels. Par exemple, il existe un modèle de code pour divers éléments que vous pourriez trouver dans le code. Il existe un modèle de document pour divers éléments de documents. Un domaine, le domaine du projet, est particulièrement intéressant pour les fournisseurs de VSPackage. Vous voudrez probablement que vos nouveaux types de projets contribuent [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] au modèle d’automatisation de la même manière que le modèle d’automatisation et contribuent au modèle d’automatisation. Ce processus est décrit dans [Fournir l’automatisation pour VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).

 Lieux où vous pouvez envisager d’étendre le modèle d’automatisation de l’environnement :

- Projet

- Document

- Code

- Générer

Pour plus d’informations sur l’automatisation, voir [Automatisation et extéabilité pour Visual Studio](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015). Ce document et les documents vers qui il fournit des liens vous aident à prendre des décisions concernant la façon dont vous devez fournir l’automatisation de votre VSPackage.

## <a name="see-also"></a>Voir aussi
- [Comment : Créer un add-in](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
