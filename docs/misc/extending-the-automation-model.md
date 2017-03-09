---
title: "Extension du mod&#232;le Automation | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèle objet Automation, étendre"
ms.assetid: f09e1365-6291-41a7-b52b-9398270d9da2
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Extension du mod&#232;le Automation
Cette section explique comment le modèle Automation et le modèle d'un VSPackage représentent une approche de deux\-fourche à l'extensibilité dans l'environnement de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  L'extensibilité consiste à améliorer et étendre les fonctionnalités de l'IDE.  L'automation, d'une part, fait référence au code créé par l'utilisateur et outils qui automatisent des tâches dans l'environnement existant et contrôlent par programme l'IDE.  VSPackages, en revanche, vous permettra d'ajouter de nouvelles fonctionnalités à l'environnement.  
  
 Il est possible de combiner l'automation et le VSPackages dans une application d'extensibilité.  Pour obtenir un exemple, consultez [Procédure pas à pas : étendre les VSPackages gérés avec l’automatisation](../misc/walkthrough-extending-managed-vspackages-by-using-automation.md).  
  
 Pour obtenir un exemple de bout en bout d'un système de projet de langage qui prend en charge le modèle Automation, consultez [Exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md).  
  
## Dans cette section  
 [Modèle Automation](/visual-cpp/misc/automation-model)  
 Fournit une vue d'ensemble du modèle Automation et explique comment le modèle Automation vous permet de personnaliser, ajuster, et automatiser l'environnement.  
  
 [Qui contribuent au modèle Automation](../extensibility/internals/contributing-to-the-automation-model.md)  
 Fournit une vue plus détaillée du modèle Automation et décrit les méthodes permettant de fournir l'automation pour votre VSPackage.  Cette section fournit également des exemples de code qui montrent comment un consommateur automation obtient les objets Automation initiaux du projet.  
  
## Rubriques connexes  
 [Kit de développement logiciel \(SDK\) Visual Studio et Automation](../Topic/Visual%20Studio%20SDK%20and%20Automation.md)  
 Traite de l'automatisation, les VSPackages, ou une combinaison pour créer des applications d'extensibilité de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .