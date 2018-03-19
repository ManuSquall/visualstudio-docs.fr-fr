---
title: "Solutions VBA et Office dans Visual Studio comparées | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: d6b2fd1cbf3ad2d58575b22b55f7ec1dc40b6ed4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Comparaison des solutions VBA et Office dans Visual Studio
  Microsoft Visual Basic pour Applications (VBA) utilise du code non managé étroitement intégré aux applications Office. Les projets Microsoft Office créés à l'aide de Visual Studio vous permettent de tirer parti des outils de conception de .NET Framework et Visual Studio.  
  
 Pour plus d’informations sur les types de solutions Office que vous pouvez créer à l’aide de Visual Studio, consultez [présentation du développement de Solutions Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="comparison"></a>Comparaison  
 Le tableau suivant répertorie les principales différences entre les solutions VBA et les solutions Office dans Visual Studio.  
  
|Solutions VBA|Solutions Office dans Visual Studio|  
|-------------------|---------------------------------------|  
|Utilisent du code qui est lié à un document spécifique et qui est stocké de façon persistante avec ce document.|Utilisent du code qui est stocké séparément du document (pour les personnalisations au niveau du document) ou dans un assembly chargé par l’application (pour les compléments VSTO).|  
|Fonctionnent avec les modèles objet Office et les API VBA.|Fournissent l'accès à la fois aux modèles objet Office et aux API [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|  
|Permettent d'enregistrer des macros et simplifient le travail du développeur.|Améliorent la sécurité, facilitent la maintenance du code et permettent l'utilisation de l'environnement de développement intégré (IDE) de Visual Studio dans son intégralité.|  
|Conviennent pour les solutions qui s'intègrent parfaitement aux applications Office.|Conviennent pour les solutions qui utilisent les ressources complètes de Visual Studio et de [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|  
|Présentent des limites d'utilisation dans l'entreprise, notamment dans les domaines de la sécurité et du déploiement.|Sont adaptées pour une utilisation dans l'entreprise.|  
  
 Certains résultats restent plus simples et plus rapides à obtenir avec VBA. En particulier, vous pouvez continuer à utiliser VBA pour :  
  
-   les fonctions de feuille de calcul personnalisées ;  
  
-   l'enregistrement de macros.  
  
## <a name="combining-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Combinaison de solutions VBA et de solutions Office créées à l'aide de Visual Studio  
 Vous pouvez appeler du code VBA à partir de solutions Office créées à l'aide de Visual Studio et, inversement, appeler du code des solutions Office créées avec Visual Studio à partir de VBA. La technique appropriée diffère selon que votre solution Office est un complément VSTO ou une personnalisation au niveau du document. Pour plus d’informations, consultez [Appel de code dans des compléments VSTO à partir d'autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) et [Combinaison de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du développement de Solutions Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Appel de Code dans des Compléments VSTO à partir d’autres Solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Combinaison de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md)   
 [Architecture des personnalisations au niveau du Document](../vsto/architecture-of-document-level-customizations.md)   
 [Architecture des Compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Sécurisation des Solutions Office](../vsto/securing-office-solutions.md)   
 [Mise en route &#40; développement Office dans Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
  
  