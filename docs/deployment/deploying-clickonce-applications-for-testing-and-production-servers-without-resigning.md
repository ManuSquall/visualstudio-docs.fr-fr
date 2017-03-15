---
title: "Deploying ClickOnce Applications For Testing and Production Servers without Resigning | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce applications, deploying without resigning"
  - "ClickOnce deployment, without resigning"
  - "application updates, ClickOnce"
  - "update location [ClickOnce]"
  - "deploymentProvider tag"
  - "manifests [ClickOnce]"
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Deploying ClickOnce Applications For Testing and Production Servers without Resigning
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique aborde une nouvelle fonctionnalité de ClickOnce présentée dans .NET Framework version 3.5 qui permet le déploiement d'applications ClickOnce à partir de plusieurs emplacements réseau sans nouvelle signature ni modification des manifestes ClickOnce.  
  
> [!NOTE]
>  La nouvelle signature reste la méthode recommandée pour le déploiement de nouvelles versions d'applications.  Dans la mesure du possible, utilisez cette méthode.  Pour plus d'informations, consultez [Mage.exe \(outil Manifest Generation and Editing\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md).  
  
 Les développeurs tiers et les éditeurs de logiciels indépendants peuvent opter pour cette fonctionnalité, qui facilite la mise à jour de leurs applications pour leurs clients.  Cette fonctionnalité peut être utilisée dans les situations suivantes :  
  
-   Lors de la mise à jour d'une application, et non lors de sa première installation.  
  
-   Lorsqu'il n'y a qu'une seule configuration de l'application sur un ordinateur.  Par exemple, si une application est configurée pour pointer vers deux bases de données différentes, vous ne pouvez pas utiliser cette fonctionnalité.  
  
## Exclusion de deploymentProvider de manifestes de déploiement  
 Dans .NET Framework 2.0 et .NET Framework 3.0, toute application ClickOnce installée sur le système pour une disponibilité hors connexion doit spécifier un `deploymentProvider` dans son manifeste de déploiement.  `deploymentProvider` est souvent désigné comme l'emplacement de mise à jour ; c'est l'emplacement dans lequel ClickOnce recherchera les mises à jour d'applications.  Cette spécification, associée à la nécessité pour les éditeurs d'applications de signer leurs déploiements, a rendu difficile pour les sociétés de mettre à jour une application ClickOnce par un fournisseur ou un tiers.  En outre, il complique davantage le déploiement de cette même application à partir de plusieurs emplacements du même réseau.  
  
 Avec les modifications apportées à ClickOnce dans .NET Framework 3.5, il est possible pour un tiers de fournir une application ClickOnce à une autre organisation, qui peut alors déployer l'application sur son propre réseau.  
  
 Pour tirer parti de cette fonctionnalité, les développeurs d'applications ClickOnce doivent exclure `deploymentProvider` de leurs manifestes de déploiement.  Cela signifie exclure l'argument `-providerUrl` lorsque vous créez des manifestes de déploiement avec Mage.exe, ou s'assurer que la zone de texte **Launch Location** sous l'onglet **Application Manifest** est vide si vous générez des manifestes de déploiement avec MageUI.exe.  
  
## deploymentProvider et mises à jour d'applications  
 À partir de .NET Framework 3.5, vous n'avez plus à spécifier un `deploymentProvider` dans votre manifeste de déploiement pour déployer une application ClickOnce en vue d'une utilisation en ligne et hors connexion.  Le scénario dans lequel vous devez empaqueter et signer vous\-même le déploiement, mais permettre à d'autres sociétés de déployer l'application sur leurs réseaux, est pris en charge.  
  
 Le point clé à retenir est que les applications qui excluent un `deploymentProvider` ne peuvent pas modifier leur emplacement d'installation pendant les mises à jour, tant qu'elles n'ont pas fourni une mise à jour qui inclut à nouveau la balise `deploymentProvider`.  
  
 Voici deux exemples qui clarifient ce point.  Dans le premier exemple, vous publiez une application ClickOnce qui n'a aucune balise `deploymentProvider`, et vous demandez aux utilisateurs de l'installer à partir de http:\/\/www.adatum.com\/MyApplication\/.  Si vous décidez de publier la mise à jour suivante de l'application à partir de http:\/\/subdomain.adatum.com\/MyApplication\/, vous n'aurez aucun moyen de le signifier dans le manifeste de déploiement qui réside dans http:\/\/www.adatum.com\/MyApplication\/.  Vous pouvez effectuer l'une des deux actions suivantes :  
  
-   Demander à vos utilisateurs de désinstaller la version antérieure, puis d'installer la nouvelle version à partir du nouvel emplacement.  
  
-   Inclure une mise à jour sur http:\/\/www.adatum.com\/MyApplication\/ qui inclut un `deploymentProvider` pointant vers http:\/\/www.adatum.com\/MyApplication\/.  Ensuite, diffuser une autre mise à jour ultérieurement, avec `deploymentProvider` pointant vers http:\/\/subdomain.adatum.com\/MyApplication\/.  
  
 Dans le second exemple, vous publiez une application ClickOnce qui spécifie `deploymentProvider`, et vous décidez ensuite de le supprimer.  Une fois que la nouvelle version sans `deploymentProvider` aura été téléchargée vers des clients, vous ne pourrez pas rediriger le chemin d'accès utilisé pour les mises à jour tant que vous n'aurez pas diffusé une version de votre application dans laquelle `deploymentProvider` aura été restauré.  Comme avec le premier exemple, `deploymentProvider` doit pointer initialement vers l'emplacement de mise à jour actuel, et non vers votre nouvel emplacement.  Dans ce cas, si vous essayez d'insérer un `deploymentProvider` qui fait référence à http:\/\/subdomain.adatum.com\/MyApplication\/, la mise à jour suivante échouera.  
  
## Création d'un déploiement  
 Pour obtenir des instructions pas à pas sur la création de déploiements qui peuvent être déployés à partir de différents emplacements réseau, consultez [Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re\-Signing and that Preserves Branding Information](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## Voir aussi  
 [Mage.exe \(outil Manifest Generation and Editing\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)