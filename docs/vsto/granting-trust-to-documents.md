---
title: Accorder un niveau de confiance à des documents
description: Découvrez comment un projet au niveau du document présente les mêmes exigences de sécurité que les projets au niveau de l’application, comme la signature des manifestes avec un certificat ou le clic sur l’invite d’approbation.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e2871741d7297b6efabf53bb6f258355c41cac49
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910256"
---
# <a name="grant-trust-to-documents"></a>Accorder un niveau de confiance à des documents
  Un projet au niveau du document présente les mêmes exigences de sécurité que les projets au niveau de l'application : il convient de signer les manifestes à l'aide d'un certificat ou de cliquer sur l'invite d'approbation. En outre, le document ou le classeur doit se trouver dans un répertoire désigné comme emplacement approuvé.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="trusted-locations"></a>Emplacements approuvés
 Les applications dans [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] et Office 2010 disposent de centres de confiance où les utilisateurs peuvent configurer des paramètres de sécurité et de confidentialité, tels que des emplacements approuvés. Pour les solutions Office, l'ordinateur local est considéré comme un emplacement approuvé. Toutefois, en raison de risques plus élevés, certains répertoires ne peuvent jamais être approuvés, tels que les dossiers temporaires système propres à chaque utilisateur et à Internet Explorer.

 Pour plus d’informations sur le centre de gestion de la confidentialité, consultez [sécurité et stratégies et paramètres dans Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)). Pour plus d’informations sur la façon de créer, gérer, supprimer et configurer des dossiers approuvés, consultez [configurer les emplacements approuvés et les paramètres éditeurs approuvés dans le système Office 2007](/previous-versions/office/office-2007-resource-kit/cc178948(v=office.12)) et [créer, supprimer ou modifier un emplacement approuvé pour vos fichiers](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

## <a name="security-considerations-for-office-solutions"></a>Considérations sur la sécurité pour les solutions Office
 Plusieurs problèmes de sécurité se posent quand vous déterminez les dossiers à ajouter aux emplacements approuvés :

- Les dossiers locaux sont considérés plus sécurisés et ils sont approuvés de manière implicite. Les emplacements distants tels que les partages de fichiers doivent être désignés comme emplacements approuvés.

- Quand vous ajoutez un répertoire aux emplacements approuvés, vous accordez une confiance totale aux solutions Office, mais également au code VBA et ActiveX. Pour cette raison, le répertoire racine et les dossiers *Mes documents* ne doivent pas être désignés comme approuvés.

- Le document lui-même est approuvé en utilisant les emplacements approuvés. Toutefois, des autorisations supplémentaires sont requises pour approuver la personnalisation. Vous pouvez accorder une confiance totale à la personnalisation en signant les manifestes à l’aide d’un certificat, en cliquant sur l’invite d’approbation ou en installant la solution Office dans le répertoire *Program Files* .

- Vous pouvez stocker le document ou le classeur d'une solution au niveau du document dans le même répertoire que l'assembly ou dans un répertoire différent. Par exemple, le document peut être situé sur un serveur SharePoint et l'assembly dans un partage de fichiers réseau. Pour plus d’informations, consultez [Comment : publier une solution Office au niveau du document sur un serveur SharePoint à l’aide de ClickOnce](/previous-versions/bb608595(v=vs.110)).

## <a name="see-also"></a>Voir aussi
- [Accorder un niveau de confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md)
- [Résoudre les problèmes de sécurité des solutions Office](../vsto/troubleshooting-office-solution-security.md)
- [Sécuriser les solutions Office](../vsto/securing-office-solutions.md)