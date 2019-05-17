---
title: Utiliser les fonctionnalités Office dans Visual Studio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c47ed9639a33ecdea3451c63b729d959f6855e5d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982326"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Utiliser les fonctionnalités Office dans Visual Studio
  Lorsque vous créez un projet au niveau du document, le document et l’application associée sont hébergés à l’intérieur de Visual Studio pour vous permettre de concevoir et de travailler directement avec le document. Lorsque vous avez une application ouverte dans Visual Studio de Microsoft Office, elle fonctionne généralement comme prévu. Toutefois, certaines fonctionnalités de l’application est différente ou inaccessible.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Protection de document
 Microsoft Office Word et Microsoft Office Excel offrent document des fonctionnalités de protection que vous pouvez utiliser dans vos projets. Toutefois, si la protection de document est activée pendant que le document est ouvert dans Visual Studio, il peut vous empêcher d’apporter des modifications de conception. Pour plus d’informations, consultez [protection dans les solutions au niveau du document dans les documents](../vsto/document-protection-in-document-level-solutions.md).

## <a name="information-rights-management"></a>Gestion des droits
 Information Rights Management (IRM) est disponible dans Microsoft Office Word et Microsoft Office Excel. IRM peut vous aider à empêcher des personnes non autorisées consultation ou modification des informations sensibles. Toutefois, IRM peut également empêcher votre code en cours d’exécution. Pour plus d’informations, consultez [Information rights management et vue d’ensemble des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md).

## <a name="password-protection"></a>Protection de mot de passe
 Documents Microsoft Office Word et classeurs Microsoft Office Excel peuvent être définis afin qu’ils ne peuvent pas être ouverts par une personne ne connaît pas le mot de passe. Protection de mot de passe est gérée différemment dans Word et Excel et peut affecter votre processus de développement. Pour plus d’informations, consultez [protection de mot de passe des documents Office](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>Voir aussi
- [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md)
- [Information rights management et vue d’ensemble des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Protection de mot de passe des documents Office](../vsto/password-protection-on-office-documents.md)
- [Guide pratique pour Ouvrir des solutions Office sans exécuter le code](../vsto/how-to-open-office-solutions-without-running-code.md)
