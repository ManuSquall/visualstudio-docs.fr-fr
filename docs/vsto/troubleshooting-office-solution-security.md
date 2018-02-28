---
title: "Résolution des problèmes de sécurité des solutions Office | Documents Microsoft"
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
- security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 2ab3571da02fa56cd905369ee44e372aedea4e36
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="troubleshooting-office-solution-security"></a>Dépannage de la sécurité des solutions Office
  Cette rubrique contient des conseils pour résoudre les problèmes courants que vous pouvez rencontrer lorsque vous travaillez avec la sécurisation des solutions Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Approuvé Solutions ne peut pas être installées à partir de Sites sensibles  
 Les utilisateurs ne peuvent pas installer une solution à partir d’un emplacement web si le site web est répertorié dans la zone sites sensibles d’Internet Explorer. Cela est vrai même si la solution est signée avec un certificat approuvé.  
  
 L’URL du manifeste de déploiement peut être classé dans une des cinq zones :  
  
-   Mon ordinateur  
  
-   Internet  
  
-   Intranet local  
  
-   Sites de confiance  
  
-   Sites sensibles  
  
 Si l’emplacement du manifeste de déploiement a été assigné à la zone sites sensibles, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] n’installe pas la solution. Si l’emplacement est connu et approuvé, l’utilisateur peut supprimer l’emplacement de la zone sites sensibles et installer la solution. Pour plus d’informations sur la gestion des zones, consultez [configuration d’éditeurs approuvés ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Solutions ne peut pas être installées à partir de partages de fichiers réseau ou des sites Web lors de la Configuration de sécurité renforcée d’Internet Explorer ou Internet Explorer 7 est installé  
 Internet Explorer Enhanced sécurité Configuration (IEESC) dans Windows Server 2003 et versions ultérieures et Internet Explorer 7 et versions ultérieur, restreint considérablement la capacité des utilisateurs à naviguer sur Internet. Lorsque les utilisateurs tentent d’installer des solutions Office à partir d’un emplacement web ou le partage de fichiers réseau, ils peuvent obtenir le message d’erreur suivant : « la fonctionnalité personnalisée dans cette application ne fonctionnera pas, car le certificat utilisé pour signer le manifeste de déploiement pour *SolutionName* n’est pas approuvé. Contactez votre administrateur pour obtenir une assistance ».  
  
 Avec IEESC et Internet Explorer 7 et versions ultérieur, si l’URL du manifeste de déploiement est classé dans la zone Internet, le manifeste doit avoir un certificat à partir d’un éditeur approuvé ou la solution ne peut pas être installée. Sans IEESC, le comportement par défaut est pour inviter l’utilisateur final à prendre une décision d’approbation.  
  
 Pour gérer l’effet d’IEESC et Internet Explorer 7 et versions supérieures, identifier les sites web et des chemins d’accès de convention (UNC) qui vous faites confiance et les ajoutez à une des zones de sécurité (intranet Local ou sites de confiance). Pour plus d’informations sur la gestion des zones, consultez [configuration d’éditeurs approuvés ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation de solutions Office](../vsto/securing-office-solutions.md)  
  
  