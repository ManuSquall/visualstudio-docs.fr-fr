---
title: Développement collaboratif de solutions Office
description: Découvrez comment plusieurs développeurs peuvent travailler sur un projet Office de la même façon qu’ils collaborent sur d’autres projets Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 028530014afdc78ab6c9c0483c3d443195383793
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942306"
---
# <a name="collaborative-development-of-office-solutions"></a>Développement collaboratif de solutions Office
  Plusieurs développeurs peuvent travailler sur un projet Office de la même façon qu’ils collaborent sur d’autres projets Visual Studio. Visual Studio localise correctement l’installation de Microsoft Office sur chaque ordinateur, même si Office est installé à différents emplacements. Toutefois, il existe des considérations importantes à prendre en compte.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>Les propriétés de débogage ne sont pas partagées
 Les propriétés de débogage ne sont pas partagées entre plusieurs utilisateurs sous contrôle de code source. Les projets Visual Basic et Visual C# stockent les propriétés de débogage dans un fichier spécifique à l’utilisateur (*ProjectName*. vbproj. User ou *ProjectName*. csproj. User), et ce fichier n’est pas sous contrôle de code source. Si plusieurs personnes effectuent un débogage, chacune d'entre elles doit entrer manuellement les propriétés de débogage.

 Si le projet est hébergé sur un partage réseau plutôt que dans le contrôle de code source, des étapes supplémentaires doivent être prises pour permettre aux développeurs de collaboration d’ouvrir la solution et de tester l’assembly.

## <a name="source-control-requires-checking-out-all-files"></a>Le contrôle de code source nécessite l’extraction de tous les fichiers
 Si vous utilisez le contrôle de code source pour vos projets, vous devez extraire tous les fichiers dans un fichier de code dans **Explorateur de solutions** (tels que les fichiers de code *ThisDocument*, *ThisWorkbook* ou *ThisAddIn* ) chaque fois que vous modifiez le fichier de code, y compris les fichiers qui sont masqués par défaut. Si vous n’extrayez que le fichier de code de niveau supérieur, vous risquez de perdre vos modifications.

 Une fois vos modifications effectuées, réactivez tous les fichiers. Pour plus d’informations sur les fichiers de code masqués dans les projets, consultez [projets Office dans l’environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="security-for-informal-collaboration-on-a-network"></a>Sécurité de la collaboration informelle sur un réseau
 Pour toutes les solutions au niveau du document qui se trouvent dans un emplacement réseau (par exemple, \\ \\ *NomServeur* \\ *Nom_Partage*), l’emplacement complet doit être ajouté à la liste des dossiers approuvés dans le Microsoft Office application que vous utilisez. Sélectionnez l’option permettant d’inclure les sous-répertoires dans le dossier principal, ou ajoutez spécifiquement les dossiers de débogage et de build dans la liste des dossiers approuvés. Pour plus d’informations sur la façon de procéder, consultez accorder un niveau [de confiance à des documents](../vsto/granting-trust-to-documents.md).

 Les certificats temporaires générés automatiquement au moment de la génération ne sont pas sécurisés par les mots de passe. Les certificats contiennent le nom de connexion du développeur et d’autres informations personnelles. Si vous déployez des personnalisations signées par des certificats temporaires, d’autres peuvent accéder à ces informations.

## <a name="see-also"></a>Voir aussi
- [Sécuriser les solutions Office](../vsto/securing-office-solutions.md)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
- [Créer des solutions Office](../vsto/building-office-solutions.md)
