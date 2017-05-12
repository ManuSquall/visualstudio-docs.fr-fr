---
title: "Comparaison des solutions VBA et Office dans Visual Studio"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "VBA (code), extensions de code managé"
  - "extensions de code managé (développement Office dans Visual Studio), comparées à VBA"
ms.assetid: 31756c2f-8829-4011-ad77-134cb3728344
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Comparaison des solutions VBA et Office dans Visual Studio
  Microsoft Visual Basic pour Applications \(VBA\) utilise du code non managé étroitement intégré aux applications Office. Les projets Microsoft Office créés à l'aide de Visual Studio vous permettent de tirer parti des outils de conception de .NET Framework et Visual Studio.  
  
 Pour plus d’informations sur les types de solutions Office que vous pouvez créer à l’aide de Visual Studio, consultez [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## Comparaison  
 Le tableau suivant répertorie les principales différences entre les solutions VBA et les solutions Office dans Visual Studio.  
  
|Solutions VBA|Solutions Office dans Visual Studio|  
|-------------------|-----------------------------------------|  
|Utilisent du code qui est lié à un document spécifique et qui est stocké de façon persistante avec ce document.|Utilisent du code qui est stocké séparément du document \(pour les personnalisations au niveau du document\) ou dans un assembly chargé par l’application \(pour les compléments VSTO\).|  
|Fonctionnent avec les modèles objet Office et les API VBA.|Fournissent l'accès à la fois aux modèles objet Office et aux API [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|  
|Permettent d'enregistrer des macros et simplifient le travail du développeur.|Améliorent la sécurité, facilitent la maintenance du code et permettent l'utilisation de l'environnement de développement intégré \(IDE\) de Visual Studio dans son intégralité.|  
|Conviennent pour les solutions qui s'intègrent parfaitement aux applications Office.|Conviennent pour les solutions qui utilisent les ressources complètes de Visual Studio et de [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|  
|Présentent des limites d'utilisation dans l'entreprise, notamment dans les domaines de la sécurité et du déploiement.|Sont adaptées pour une utilisation dans l'entreprise.|  
  
 Certains résultats restent plus simples et plus rapides à obtenir avec VBA. En particulier, vous pouvez continuer à utiliser VBA pour :  
  
-   les fonctions de feuille de calcul personnalisées ;  
  
-   l'enregistrement de macros.  
  
## Combinaison de solutions VBA et de solutions Office créées à l'aide de Visual Studio  
 Vous pouvez appeler du code VBA à partir de solutions Office créées à l'aide de Visual Studio et, inversement, appeler du code des solutions Office créées avec Visual Studio à partir de VBA. La technique appropriée diffère selon que votre solution Office est un complément VSTO ou une personnalisation au niveau du document. Pour plus d’informations, consultez [Appel de code dans des compléments VSTO à partir d'autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) et [Combinaison de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md).  
  
## Voir aussi  
 [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Appel de code dans des compléments VSTO à partir d'autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Combinaison de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md)   
 [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md)   
 [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Sécurisation des solutions Office](../vsto/securing-office-solutions.md)   
 [Mise en route &#40;Développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
  
  