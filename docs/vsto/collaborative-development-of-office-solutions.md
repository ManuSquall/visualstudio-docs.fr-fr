---
title: Développement collaboratif de solutions Office
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 76c26a110d88d3dee8bf7540647ea0bfde4e7c4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949485"
---
# <a name="collaborative-development-of-office-solutions"></a>Développement collaboratif de solutions Office
  Plusieurs développeurs peuvent travailler sur un projet Office de la même façon qu’ils collaborent sur d’autres projets Visual Studio. Visual Studio localise correctement l’installation de Microsoft Office sur chaque ordinateur, même si Office est installé dans des emplacements différents. Toutefois, il existe quelques considérations importantes à connaître.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>Déboguer des propriétés ne sont pas partagées
 Les propriétés de débogage ne sont pas partagées entre plusieurs utilisateurs sous contrôle de code source. Visual Basic et Visual C# projets stockent les propriétés de débogage dans un fichier spécifique à l’utilisateur (*nom_projet*. vbproj.user ou *nom_projet*. csproj.user), et ce fichier n’est pas sous contrôle de code source . Si plusieurs personnes effectuent un débogage, chacune d'entre elles doit entrer manuellement les propriétés de débogage.

 Si le projet est hébergé sur un partage réseau au lieu de contrôle de code source, certaines étapes supplémentaires doivent être prises pour permettre aux développeurs travaillant en collaboration ouvrir la solution et de l’assembly de test.

## <a name="source-control-requires-checking-out-all-files"></a>Requiert de l’extraction de tous les fichiers de contrôle de code source
 Si vous utilisez le contrôle de code source pour vos projets, vous devez extraire tous les fichiers sous un fichier de code dans **l’Explorateur de solutions** (telles que la *ThisDocument*, *ThisWorkbook*, ou *ThisAddIn* fichiers de code) chaque fois que vous modifiez le fichier de code, y compris les fichiers qui sont masqués par défaut. Si vous extrayez uniquement le fichier de code de niveau supérieur, vos modifications peuvent être perdues.

 Après avoir apporté vos modifications, archiver tous les fichiers. Pour plus d’informations sur les fichiers de code caché dans des projets, consultez [les projets Office dans l’environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="security-for-informal-collaboration-on-a-network"></a>Sécurité pour une collaboration informelle sur un réseau
 Pour toutes les solutions au niveau du document qui se trouvent dans un emplacement réseau (tel que \\ \\ *nom_serveur*\\*nom_partage*), l’emplacement qualifié complet doit être ajouté à la liste des dossiers approuvés dans l’application Microsoft Office que vous utilisez. Sélectionnez l’option pour inclure les sous-répertoires sous le dossier principal, ou plus précisément ajoutez debug et créer des dossiers à la liste des dossiers approuvés. Pour plus d’informations sur la procédure à suivre, consultez [accorder une confiance aux documents](../vsto/granting-trust-to-documents.md).

 Les certificats temporaires qui sont automatiquement générées au moment de la génération ne sont pas sécurisés par les mots de passe. Les certificats contiennent le nom de connexion du développeur et d’autres informations personnelles. Si vous déployez des personnalisations qui sont signées par des certificats temporaires, il se peut que d’autres peuvent être en mesure d’accéder à ces informations.

## <a name="see-also"></a>Voir aussi
- [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
- [Générer des solutions Office](../vsto/building-office-solutions.md)
