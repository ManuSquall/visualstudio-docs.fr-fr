---
title: Vue d’ensemble du modèle Automation | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a9369bb6074bb294223051ba7dfa158648fe0cad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134745"
---
# <a name="automation-model-overview"></a>Vue d’ensemble du modèle Automation
Le modèle automation se compose d’un ensemble d’objets par rapport à laquelle vous pouvez écrire un complément Visual Studio ou une extension. Un complément est une application qui peut manipuler l’environnement Visual Studio et automatiser les tâches courantes. Une extension Visual Studio peut créer des composants personnalisés de Visual Studio ou ajouter des fonctionnalités de composants standard tels que l’éditeur de texte.  
  
## <a name="objects-in-the-automation-model"></a>Objets dans le modèle Automation  
 Le modèle automation se compose de groupes associés d’objets qui contrôlent les aspects de l’environnement du common. Voici un diagramme qui affiche l’ensemble complet des objets qui composent le modèle automation.  
  
 ![Le graphique d’objet Automation Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Objets automation Visual Studio  
  
 Pour plus d’informations, consultez [étendre l’environnement Visual Studio](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 L’environnement fournit un modèle pour les différentes zones fonctionnelles. Par exemple, il est un modèle de code pour différents éléments qui peuvent s’avérer dans le code. Il existe un modèle de document pour les différents éléments du document. Une zone, la zone de projet, est particulièrement intéressant pour les fournisseurs de VSPackage. Il est probable que vos nouveaux types de projets qui contribuent au modèle automation de la même façon en tant que [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuent au modèle automation. Que le processus est décrit dans [qui fournit l’Automation pour les VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Emplacements où vous pouvez envisager d’étendre le modèle automation de l’environnement :  
  
-   Projet  
  
-   Document  
  
-   Code  
  
-   Générer  
  
 Pour plus d’informations sur l’automatisation, consultez [automatisation et extensibilité pour Visual Studio](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Ce document et les documents fournit des liens pour vous aider à prendre des décisions concernant la manière dont vous devez fournir l’automatisation pour votre VSPackage.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer un complément](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)