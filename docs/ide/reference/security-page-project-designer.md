---
title: "Page S&#233;curit&#233;, Concepteur de projets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesSecurity"
  - "vb.XBAPProjectPropertiesSecurity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Concepteur de projets, page Sécurité"
  - "Page Sécurité du Concepteur de projets"
ms.assetid: 641d9cd3-fa07-498a-8568-3c169bb4d3d5
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Page S&#233;curit&#233;, Concepteur de projets
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La page **Sécurité** du **Concepteur de projets** permet de configurer les paramètres de sécurité d'accès du code pour les applications qui sont déployées à l'aide du déploiement de [!INCLUDE[ndptecclick](../../deployment/includes/ndptecclick_md.md)].  Pour plus d'informations, consultez [Sécurité d'accès du code pour les applications ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Pour accéder à la page **Sécurité**, cliquez sur un nœud de projet dans l'**Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**.  Lorsque le **Concepteur de projets** apparaît, cliquez sur l'onglet **Sécurité**.  
  
## Paramètres de sécurité  
 **Activer les paramètres de sécurité ClickOnce**  
 Détermine si les paramètres de sécurité sont activés au moment du design.  Si cette option est désactivée, aucune autre option de la page **Sécurité** n'est disponible.  
  
> [!NOTE]
>  Lors de la publication d'une application à l'aide de l'Assistant **Publication**, cette option est automatiquement activée.  
  
 Si vous activez cette option, vous pouvez sélectionner l'une des deux cases d'option : **Il s'agit d'une application de confiance totale** ou **Il s'agit d'une application de confiance partielle**.  
  
 Cette option est sélectionnée par défaut pour les projets d'application de navigateur Web WPF.  
  
 Cette option est désactivée par défaut pour tous les autres types de projet.  
  
 **Il s'agit d'une application de confiance totale**  
 Si vous sélectionnez cette option, l'application demande des autorisations Confiance totale lorsqu'elle est installée ou exécutée sur un ordinateur client.  Évitez d'utiliser la Confiance totale, car un accès illimité aux ressources, telles que le système de fichiers et le Registre, sera accordé à votre application.  
  
 Par défaut, cette option a la valeur Confiance partielle pour les projets d'application de navigateur Web WPF.  
  
 Par défaut, cette option a la valeur Confiance totale pour tous les autres types de projet.  
  
 **Il s'agit d'une application de confiance partielle**  
 Si vous sélectionnez cette option, l'application demande des autorisations Confiance partielle lorsqu'elle est installée ou exécutée sur un ordinateur client.  *La Confiance partielle* signifie que seules les actions autorisées sous les autorisations de sécurité d'accès du code demandées s'exécuteront.  Pour plus d'informations sur la configuration d'autorisations de sécurité, consultez [Sécurité d'accès du code pour les applications ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Vous pouvez spécifier les paramètres de sécurité de Confiance partielle en configurant les options dans la zone **Autorisations de sécurité ClickOnce**.  
  
## Autorisations de sécurité ClickOnce  
 **Zone à partir de laquelle votre application sera installée**  
 Spécifie un jeu par défaut d'autorisations de sécurité d'accès du code.  Choisissez **Internet** ou **Intranet local** pour un ensemble d'autorisations restreintes ou choisissez **\(Personnalisé\)** pour configurer un ensemble d'autorisations personnalisées.  Si l'application demande plus d'autorisations que celles accordées dans une zone, une invite d'approbation ClickOnce s'affiche pour l'utilisateur final pour accorder les autorisations supplémentaires.  Pour plus d'informations sur la configuration d'autorisations de sécurité, consultez [Sécurité d'accès du code pour les applications ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Par défaut; cette option a la valeur **Internet** pour les projets d'application de navigateur Web WPF.  
  
 **Modifier les autorisations XML**  
 Ouvre le modèle de manifeste de l'application \(app.manifest\) pour configurer les autorisations pour le jeu d'autorisations **\(Personnalisé\)**.  
  
 **Avancé**  
 Ouvre la [Paramètres de sécurité avancés, boîte de dialogue](../../ide/reference/advanced-security-settings-dialog-box.md) qui permet de configurer les paramètres pour déboguer les applications avec des autorisations restreintes.  Ces paramètres sont vérifiés pendant le débogage, et les exceptions d'autorisation indiquent que votre application peut avoir besoin de plus d'autorisations que défini dans une zone.  
  
## Voir aussi  
 <xref:System.Security.Permissions.WebBrowserPermission>   
 <xref:System.Security.Permissions.MediaPermission>   
 [Sécurité d'accès du code pour les applications ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md)   
 [How to: Enable ClickOnce Security Settings](../../deployment/how-to-enable-clickonce-security-settings.md)   
 [Comment : définir une zone de sécurité pour une application ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Comment : définir des autorisations personnalisées pour une application ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Comment : déboguer une application ClickOnce avec des autorisations restreintes](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [ClickOnce Security and Deployment](../../deployment/clickonce-security-and-deployment.md)   
 [Référence de propriétés de projet](../../ide/reference/project-properties-reference.md)   
 [Paramètres de sécurité avancés, boîte de dialogue](../../ide/reference/advanced-security-settings-dialog-box.md)