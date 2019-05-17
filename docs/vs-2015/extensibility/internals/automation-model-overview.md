---
title: Vue d’ensemble du modèle Automation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e17164976062ec916074c6210be6ae42e8ea1d03
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699507"
---
# <a name="automation-model-overview"></a>Modèle d’automatisation
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le modèle automation se compose d’un ensemble d’objets par rapport à laquelle vous pouvez écrire un complément Visual Studio ou une extension. Un complément est une application qui peut manipuler l’environnement Visual Studio et automatiser les tâches courantes. Une extension Visual Studio peut créer des composants personnalisés de Visual Studio ou ajouter des fonctionnalités de composants standard tels que l’éditeur de texte.  
  
## <a name="objects-in-the-automation-model"></a>Objets dans le modèle Automation  
 Le modèle automation se compose de groupes connexes d’objets qui contrôlent les aspects de l’environnement du common. Voici un diagramme qui montre l’ensemble complet d’objets qui composent le modèle automation.  
  
 ![Le graphique d’objet Automation Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Objets automation Visual Studio  
  
 Pour plus d’informations, consultez [étendre l’environnement Visual Studio](https://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 L’environnement fournit un modèle pour les différentes zones fonctionnelles. Par exemple, il est un modèle de code pour divers éléments que vous pouvez trouver dans le code. Il existe un modèle de document pour différents éléments de document. Une zone, la zone de projet est un intérêt particulier pour les fournisseurs de VSPackage. Il est probable que vos nouveaux types de projet pour contribuer au modèle automation dans la même façon que [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] et [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] contribuer au modèle automation. Que le processus est décrit dans [fournissant l’automatisation pour VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Endroits où vous pouvez envisager d’extension du modèle automation de l’environnement :  
  
- Projet  
  
- Document  
  
- Code  
  
- Build  
  
  Pour plus d’informations sur l’automatisation, consultez [automatisation et extensibilité pour Visual Studio](https://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Ce document et les documents, il fournit des liens pour vous aider à prendre des décisions concernant la façon dont vous devez fournir l’automation pour votre VSPackage.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Créer un complément](https://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
