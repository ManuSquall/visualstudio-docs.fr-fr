---
title: Utiliser les fonctionnalités Office dans Visual Studio
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6a1db785b4758236c4a50e694d868cecc269324a
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767505"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Utiliser les fonctionnalités Office dans Visual Studio
  Lorsque vous créez un projet au niveau du document, le document et l’application associée sont hébergés au sein de Visual Studio afin de pouvoir concevoir et travailler directement avec le document. Lorsque vous avez une application ouvre dans Visual Studio de Microsoft Office, fonctionne généralement comme prévu. Toutefois, certaines fonctionnalités de l’application est différent ou est inaccessible.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="document-protection"></a>Protection du document  
 Microsoft Office Word et Microsoft Office Excel offrent document des fonctionnalités de protection que vous pouvez utiliser dans vos projets. Toutefois, si la protection de document est activée alors que le document est ouvert dans Visual Studio, il peut vous empêcher d’apporter des modifications de conception. Pour plus d’informations, consultez [protection dans les solutions au niveau du document des documents](../vsto/document-protection-in-document-level-solutions.md).  
  
## <a name="information-rights-management"></a>Gestion des droits  
 Information Rights Management (IRM) est disponible dans Microsoft Office Word et Microsoft Office Excel. IRM peut vous aider à empêcher les personnes non autorisées d’affichage ou la modification d’informations sensibles. Toutefois, IRM peut également empêcher votre code en cours d’exécution. Pour plus d’informations, consultez [Information rights management et vue d’ensemble des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md).  
  
## <a name="password-protection"></a>Mot de passe  
 Les documents Microsoft Office Word et classeurs Microsoft Office Excel peuvent être définis afin qu’ils ne peuvent pas être ouverts par une personne ne connaît pas le mot de passe. Mot de passe est géré différemment dans Word et Excel et peut affecter votre processus de développement. Pour plus d’informations, consultez [mot de passe sur des documents Office](../vsto/password-protection-on-office-documents.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md)   
 [Information rights management et vue d’ensemble des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Mot de passe sur des documents Office](../vsto/password-protection-on-office-documents.md)   
 [Comment : les solutions Office ouvrir sans exécuter du code](../vsto/how-to-open-office-solutions-without-running-code.md)  
  
  