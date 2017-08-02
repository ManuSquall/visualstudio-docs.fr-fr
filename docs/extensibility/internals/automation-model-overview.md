---
title: "Vue d’ensemble du modèle Automation | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: ce59c002accd55b9179cacc60cf944ff72138c7e
ms.lasthandoff: 02/22/2017

---
# <a name="automation-model-overview"></a>Vue d’ensemble du modèle Automation
Le modèle automation se compose d’un ensemble d’objets par rapport à laquelle vous pouvez écrire un complément Visual Studio ou une extension. Un complément est une application qui peut manipuler l’environnement Visual Studio et automatiser les tâches courantes. Une extension Visual Studio peut créer des composants Visual Studio personnalisés ou ajouter des fonctionnalités des composants standards tels que l’éditeur de texte.  
  
## <a name="objects-in-the-automation-model"></a>Objets dans le modèle Automation  
 Le modèle automation se compose de groupes d’objets qui contrôlent les aspects de l’environnement du common liés. Voici un diagramme qui montre le large éventail d’objets qui composent le modèle automation.  
  
 ![Graphique d’objet Automation Visual Studio](~/extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Objets automation Visual Studio  
  
 Pour plus d’informations, consultez [extension de l’environnement Visual Studio](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 L’environnement fournit un modèle pour les différentes zones fonctionnelles. Par exemple, il est un modèle de code pour différents éléments que vous pouvez trouver dans le code. Il existe un modèle de document pour les différents éléments du document. Une seule zone, la zone de projet, est particulièrement intéressant pour les fournisseurs VSPackage. Il est probable que vos nouveaux types de projet pour contribuer au modèle automation de la même façon en tant que [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuent au modèle automation. Que le processus est décrit dans [fournissant l’automatisation VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Endroits où vous pouvez envisager d’étendre le modèle automation de l’environnement :  
  
-   Projet  
  
-   Document  
  
-   Code  
  
-   Build  
  
 Pour plus d’informations sur l’automatisation, consultez [automatisation et extensibilité pour Visual Studio](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Ce document et les documents propose des liens pour vous aider à prendre des décisions concernant la, vous devez fournir l’automatisation votre VSPackage.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer un complément](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
