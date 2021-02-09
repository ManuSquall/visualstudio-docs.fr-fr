---
title: Protection par mot de passe sur les documents Office
description: Découvrez comment définir un mot de passe pour vos documents Microsoft Word et vos classeurs Excel afin qu’ils ne puissent pas être ouverts par des utilisateurs non autorisés.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2cc320baf310af0ec2b4cdd84fabff951b2a9cb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885285"
---
# <a name="password-protection-on-office-documents"></a>Protection par mot de passe sur les documents Office
  Il est possible de définir un mot de passe dans vos documents Word Microsoft Office et Microsoft Office classeurs Excel afin qu’ils ne puissent pas être ouverts par une personne qui ne connaît pas le mot de passe. Cette option est appelée **mot de passe à l’ouverture**.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Vous pouvez créer des projets au niveau du document à l’aide de documents et classeurs existants dont **le mot de passe** est activé. Le comportement dans Visual Studio est différent pour les documents Word et Excel dont le **mot de passe** est activé.

 Pour plus d’informations sur l’activation du **mot de passe à l’ouverture**, consultez aide dans Word ou Excel.

## <a name="behavior-of-excel-and-word"></a>Comportement d’Excel et de Word
 Chaque fois que vous ouvrez un classeur Excel dans Visual Studio pour lequel le **mot de passe** est activé, Excel vous invite à entrer le mot de passe. Lorsque vous générez votre solution, vous êtes invité à entrer à nouveau le mot de passe, car le document est ouvert pendant la génération.

 La première fois que vous ouvrez un document Word dans Visual Studio pour lequel le **mot de passe** est activé, Word vous invite à entrer le mot de passe. Une fois que vous avez entré le mot de passe, le **mot de passe à l’ouverture** est supprimé du document et l’ouverture du document n’a plus besoin d’un mot de passe. Si vous souhaitez que le document dans votre solution exige un mot de passe avant de pouvoir être ouvert, vous devez activer le **mot de passe à l’ouverture** après votre Build finale et avant de déployer la solution.

## <a name="see-also"></a>Voir aussi
- [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md)
- [Présentation de la gestion des droits relatifs à l’information et des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Comment : autoriser le code à s’exécuter derrière des documents avec des autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
