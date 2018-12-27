---
title: Accorder votre confiance à des documents
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: e1fb856897f4db39fb41875f3230603237f0cc0b
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648832"
---
# <a name="grant-trust-to-documents"></a>Accorder votre confiance à des documents
  Un projet au niveau du document présente les mêmes exigences de sécurité que les projets au niveau de l’application : il convient de signer les manifestes à l’aide d’un certificat ou de cliquer sur l’invite d’approbation. En outre, le document ou le classeur doit se trouver dans un répertoire désigné comme emplacement approuvé.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>Emplacements approuvés  
 Applications dans [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] et Office 2010 disposent de centres de confiance dans lequel les utilisateurs peuvent configurer les paramètres de sécurité, telles que les emplacements approuvés. Pour les solutions Office, l’ordinateur local est considéré comme un emplacement approuvé. Toutefois, en raison de risques plus élevés, certains répertoires ne peuvent jamais être approuvés, tels que les dossiers temporaires système propres à chaque utilisateur et à Internet Explorer.  
  
 Pour plus d’informations sur le centre de confidentialité, consultez [sécurité et les stratégies et les paramètres dans Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202). Pour plus d’informations sur la façon de créer, gérer, supprimer et configurer des dossiers approuvés, consultez [configurer les paramètres des emplacements et éditeurs approuvés dans Office system 2007](http://go.microsoft.com/fwlink/?LinkId=89203) et [créer, supprimer ou modifier un emplacement pour vos fichiers approuvé](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="security-considerations-for-office-solutions"></a>Considérations sur la sécurité pour les solutions Office  
 Plusieurs problèmes de sécurité se posent quand vous déterminez les dossiers à ajouter aux emplacements approuvés :  
  
-   Les dossiers locaux sont considérés plus sécurisés et ils sont approuvés de manière implicite. Les emplacements distants tels que les partages de fichiers doivent être désignés comme emplacements approuvés.  
  
-   Quand vous ajoutez un répertoire aux emplacements approuvés, vous accordez une confiance totale aux solutions Office, mais également au code VBA et ActiveX. Pour cette raison, le répertoire racine et le *Mes Documents* dossiers ne doivent pas être désignés comme étant fiables.  
  
-   Le document lui-même est approuvé en utilisant les emplacements approuvés. Toutefois, des autorisations supplémentaires sont requises pour approuver la personnalisation. Vous pouvez accorder une confiance totale à la personnalisation à l’aide de la signature des manifestes avec un certificat, en cliquant sur l’invite d’approbation ou l’installation de la solution Office à le *Program Files* directory.  
  
-   Vous pouvez stocker le document ou le classeur d'une solution au niveau du document dans le même répertoire que l'assembly ou dans un répertoire différent. Par exemple, le document peut être situé sur un serveur SharePoint et l'assembly dans un partage de fichiers réseau. Pour plus d'informations, voir [Procédure : Publier une solution de Office au niveau du document sur un serveur SharePoint à l’aide de ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## <a name="see-also"></a>Voir aussi  
 [Accorder votre confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md)   
 [Résoudre les problèmes de sécurité des solutions Office](../vsto/troubleshooting-office-solution-security.md)   
 [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)  
  
  