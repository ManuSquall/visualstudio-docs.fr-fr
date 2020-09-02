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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62982326"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Utiliser les fonctionnalités Office dans Visual Studio
  Lorsque vous créez un projet au niveau du document, le document et l’application associée sont hébergés dans Visual Studio afin que vous puissiez concevoir et travailler directement avec le document. Lorsque vous avez une application Microsoft Office ouverte dans Visual Studio, elle fonctionne généralement comme prévu. Toutefois, certaines fonctionnalités de l’application sont différentes ou inaccessibles.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Protection des documents
 Microsoft Office Word et Microsoft Office Excel offrent des fonctionnalités de protection de document que vous pouvez utiliser dans vos projets. Toutefois, si la protection des documents est activée alors que le document est ouvert dans Visual Studio, cela peut vous empêcher de modifier la conception. Pour plus d’informations, consultez [protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md).

## <a name="information-rights-management"></a>Gestion des droits relatifs à l’information
 Les informations Rights Management (IRM) sont disponibles dans Microsoft Office Word et Microsoft Office Excel. IRM peut vous aider à empêcher des personnes non autorisées d’afficher ou de modifier des informations sensibles. Toutefois, IRM peut également empêcher l’exécution de votre code. Pour plus d’informations, consultez [vue d’ensemble de la gestion des droits relatifs à l’information et des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md).

## <a name="password-protection"></a>Protection par mot de passe
 Microsoft Office les documents Word et Microsoft Office classeurs Excel peuvent être définis de sorte qu’ils ne puissent pas être ouverts par une personne qui ne connaît pas le mot de passe. La protection par mot de passe est gérée différemment dans Word et Excel, et peut affecter votre processus de développement. Pour plus d’informations, consultez [protection par mot de passe sur les documents Office](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>Voir aussi
- [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md)
- [Présentation de la gestion des droits relatifs à l’information et des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Protection par mot de passe sur les documents Office](../vsto/password-protection-on-office-documents.md)
- [Comment : ouvrir des solutions Office sans exécuter de code](../vsto/how-to-open-office-solutions-without-running-code.md)
