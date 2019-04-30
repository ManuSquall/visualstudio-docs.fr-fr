---
title: Résoudre les problèmes de sécurité des solutions Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 921bef3514b802672296dda6d680b665f1f42482
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978313"
---
# <a name="troubleshoot-office-solution-security"></a>Résoudre les problèmes de sécurité des solutions Office
  Cette rubrique contient des conseils pour résoudre les problèmes courants que vous pouvez rencontrer lorsque vous travaillez avec la sécurisation des solutions Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Solutions approuvées ne peut pas être installées à partir de sites sensibles
 Les utilisateurs ne peuvent pas installer une solution à partir d’un emplacement web si le site Web est répertorié dans la zone de sites sensibles d’Internet Explorer. Cela est vrai même si la solution est signée avec un certificat approuvé.

 L’URL du manifeste de déploiement peut être classé dans une des cinq zones :

- Mon ordinateur

- Internet

- Intranet local

- Sites de confiance

- Sites sensibles

  Si l’emplacement du manifeste de déploiement a été assigné à la zone sites sensibles, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] n’installe pas la solution. Si l’emplacement est connu et approuvé, l’utilisateur peut supprimer l’emplacement de la zone sites sensibles et installer la solution. Pour plus d’informations sur la façon de gérer des zones, consultez [configuration d’éditeurs approuvés ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Solutions ne peut pas être installées à partir de partages de fichiers réseau ou des emplacements web lorsque la Configuration de sécurité renforcée d’Internet Explorer ou Internet Explorer 7 est installé
 Internet Explorer Enhanced Security Configuration (IEESC) dans Windows Server 2003 et versions ultérieures et Internet Explorer 7 et versions ultérieure, restreint considérablement la capacité des utilisateurs à naviguer sur Internet. Lorsque les utilisateurs essaient d’installer partagent des solutions Office à partir d’un fichier de réseau ou l’emplacement web, ils peuvent obtenir le message d’erreur suivant : « La fonctionnalité personnalisée dans cette application ne fonctionnera pas, car le certificat utilisé pour signer le manifeste de déploiement pour *SolutionName* n’est pas approuvé. Contactez votre administrateur pour obtenir une assistance supplémentaire. »

 Avec IEESC et Internet Explorer 7 et versions ultérieure, si l’URL du manifeste de déploiement est classé dans la zone Internet, le manifeste doit avoir un certificat à partir d’un éditeur approuvé ou la solution ne peut pas être installée. Sans IEESC, le comportement par défaut est pour inviter l’utilisateur final à prendre une décision d’approbation.

 Pour gérer l’effet d’IEESC et Internet Explorer 7 et versions ultérieures, identifier les sites Web et des chemins d’accès UNC (convention) qui vous faites confiance et les ajoutez à une des zones de sécurité (intranet Local ou sites de confiance). Pour plus d’informations sur la façon de gérer des zones, consultez [éditeurs dignes de confiance ClickOnce configurer](http://go.microsoft.com/fwlink/?LinkId=94774).

## <a name="see-also"></a>Voir aussi
- [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)
