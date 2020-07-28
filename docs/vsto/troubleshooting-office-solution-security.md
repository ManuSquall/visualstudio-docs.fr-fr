---
title: Résoudre les problèmes de sécurité des solutions Office
ms.date: 02/02/2017
ms.topic: troubleshooting
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
ms.openlocfilehash: 8825f1f4393d93df6a621fd71b6782c6652a9c0c
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234807"
---
# <a name="troubleshoot-office-solution-security"></a>Résoudre les problèmes de sécurité des solutions Office
  Cette rubrique contient des conseils pour résoudre les problèmes courants que vous pouvez rencontrer lorsque vous utilisez la sécurisation des solutions Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Les solutions approuvées ne peuvent pas être installées à partir de sites sensibles
 Les utilisateurs ne peuvent pas installer une solution à partir d’un emplacement Web si le site Web est listé dans la zone sites sensibles d’Internet Explorer. Cela est vrai même si la solution est signée avec un certificat approuvé.

 L’URL du manifeste de déploiement peut être classée dans l’une des cinq zones suivantes :

- Poste de travail

- Internet

- Intranet local

- Sites de confiance

- Sites sensibles

  Si l’emplacement du manifeste de déploiement a été affecté à la zone des sites sensibles, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] n’installe pas la solution. Si l’emplacement est connu et peut être approuvé, l’utilisateur peut supprimer l’emplacement de la zone des sites sensibles et installer la solution. Pour plus d’informations sur la gestion des zones, consultez [Configuration des éditeurs approuvés ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Les solutions ne peuvent pas être installées à partir de partages de fichiers réseau ou d’emplacements Web lors de l’installation de la configuration de sécurité renforcée d’Internet Explorer ou d’Internet Explorer 7
 La configuration de sécurité renforcée d’Internet Explorer (IEESC) dans Windows Server 2003 et versions ultérieures, et Internet Explorer 7 et versions ultérieures, limite considérablement la capacité des utilisateurs à naviguer sur Internet. Quand les utilisateurs essaient d’installer des solutions Office à partir d’un partage de fichiers réseau ou d’un emplacement Web, ils peuvent obtenir le message d’erreur suivant : «les fonctionnalités personnalisées de cette application ne fonctionneront pas, car le certificat utilisé pour signer le manifeste de déploiement pour *NomSolution* n’est pas approuvé. Contactez votre administrateur pour obtenir de l’aide.»

 Avec IEESC et Internet Explorer 7 et versions ultérieures, si l’URL du manifeste de déploiement est catégorisée dans la zone Internet, le manifeste doit avoir un certificat provenant d’un éditeur approuvé ou la solution ne peut pas être installée. Sans IEESC, le comportement par défaut consiste à inviter l’utilisateur final à prendre une décision d’approbation.

 Pour gérer l’effet de IEESC et d’Internet Explorer 7 et versions ultérieures, identifiez les sites Web et les chemins d’accès UNC (Universal Naming Convention) auxquels vous faites confiance et ajoutez-les à l’une des zones de sécurité approuvées (Intranet local ou sites de confiance). Pour plus d’informations sur la gestion des zones, consultez [configurer des éditeurs approuvés ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="see-also"></a>Voir aussi
- [Sécuriser les solutions Office](../vsto/securing-office-solutions.md)
- [Résolution des problèmes de Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
