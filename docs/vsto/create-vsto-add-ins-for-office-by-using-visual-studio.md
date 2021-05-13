---
title: Créer des compléments VSTO pour Office à l'aide de Visual Studio
description: Découvrez comment vous pouvez utiliser les outils de développement Microsoft Office dans Visual Studio pour créer des applications .NET Framework qui étendent Office.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 04/28/2021
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 990caeec642a745bec5b6e0f2d29ff5d6213d095
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848316"
---
# <a name="create-vsto-add-ins-for-office-by-using-visual-studio"></a>Créer des compléments VSTO pour Office à l'aide de Visual Studio
> [!IMPORTANT]
> VSTO s’appuie sur le [.NET Framework](https://docs.microsoft.com/dotnet/framework/get-started/overview). Les compléments COM peuvent également être écrits avec l' .NET Framework. Impossible de créer des compléments Office avec [.net Core et .net 5 +](https://docs.microsoft.com/dotnet/core/dotnet-five), les dernières versions de .net. Cela est dû au fait que .NET Core/. NET 5 + ne peut pas fonctionner conjointement avec .NET Framework dans le même processus et peut entraîner des échecs de chargement de complément. Vous pouvez continuer à utiliser .NET Framework pour écrire des compléments VSTO et COM pour Office. Microsoft ne mettra pas à jour VSTO ou la plateforme de complément COM pour utiliser .NET Core ou .NET 5 +. Vous pouvez tirer parti de .NET Core et de .NET 5 +, y compris ASP.NET Core, pour créer le côté serveur des [compléments Web Office](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins).

  Vous pouvez utiliser les outils de développement Microsoft Office dans Visual Studio pour créer des applications .NET Framework qui étendent Office. Ces applications sont également appelées *solutions Office*.

 Les outils de développement Office fournissent des fonctionnalités qui permettent de créer des solutions Office pour répondre à différents besoins professionnels. Ces outils incluent des modèles de projet pour vous aider à créer des solutions Office à l'aide de Visual Basic ou de Visual C#, et des concepteurs visuels qui vous aident à créer des interfaces utilisateur personnalisées pour vos solutions Office.

[!include[Add-ins note](includes/addinsnote.md)]

 Pour obtenir les informations les plus récentes sur le développement Office, consultez le [Centre de développement Microsoft Office](https://developer.microsoft.com/office/docs).

## <a name="in-this-section"></a>Contenu de cette section
- [Prise en main &#40;le développement Office dans Visual Studio&#41;](getting-started-office-development-in-visual-studio.md)

 Fournit des liens vers des informations relatives à la configuration d'un ordinateur de développement pour créer des solutions Office, à la mise en route pour créer des solutions Office et aux nouveautés du développement Office dans Visual Studio.

- [Mettre à niveau et migrer des solutions Office](upgrading-and-migrating-office-solutions.md)

 Fournit des liens vers des informations relatives au processus de mise à niveau pour les projets créés à l'aide de versions antérieures de Visual Studio.

- [Architecture des solutions Office dans Visual Studio](architecture-of-office-solutions-in-visual-studio.md)

 Fournit des liens vers des informations sur le fonctionnement des solutions Office, notamment des informations sur les personnalisations au niveau du document et les compléments VSTO.

- [Concevoir et créer des solutions Office](designing-and-creating-office-solutions.md)

 Fournit des informations sur la création d'un projet Office et la configuration de votre projet dans Visual Studio.

- [Développer des solutions Office](developing-office-solutions.md)

 Fournit des informations sur l'utilisation de code managé avec les solutions Office, notamment sur la personnalisation de l'interface utilisateur Office, l'utilisation des données et la résolution des problèmes.

- [Solutions Excel](excel-solutions.md)

 Fournit des informations sur l'automatisation d'Excel, la création de solutions Excel et la compréhension de problèmes de globalisation spécifiques à Excel.

- [Solutions InfoPath](infopath-solutions.md)

 Fournit des informations sur la création de modèles de formulaire et de compléments VSTO pour InfoPath.

- [Solutions Outlook](outlook-solutions.md)

 Fournit des informations sur l'automatisation d'Outlook, et sur la création de compléments et de zones de formulaire VSTO Outlook.

- [Solutions PowerPoint](powerpoint-solutions.md)

 Fournit des informations sur l'automatisation de PowerPoint et sur la création de compléments VSTO PowerPoint.

- [Solutions de projet](project-solutions.md)

 Fournit des informations sur l’automatisation d’Microsoft Office projet et la création de compléments VSTO Project.

- [Solutions Visio](visio-solutions.md)

 Fournit des informations sur l'automatisation de Visio et sur la création de compléments VSTO Visio.

- [Solutions Word](word-solutions.md)

 Fournit des informations sur l'automatisation de Word et la création de solutions Word.

- [Créer des solutions Office](building-office-solutions.md)

 Fournit des informations sur les différences entre la génération de projets Office et d'autres types de projets dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [Déboguer des projets Office](debugging-office-projects.md)

 Fournit des informations sur les différences entre le débogage de projets Office et d'autres types de projets dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [Sécuriser les solutions Office](securing-office-solutions.md)

 Fournit des informations sur le fonctionnement de fonctionnalités de sécurité dans les solutions Office.

- [Déployer une solution Office](deploying-an-office-solution.md)

 Fournit des informations sur la façon de rendre des solutions Office accessibles à vos utilisateurs, ainsi que sur les principaux problèmes à prendre en considération lors du choix d'une méthode de déploiement.

- [Exemples et procédures pas à pas relatifs au développement Office](office-development-samples-and-walkthroughs.md)

 Fournit des liens vers des exemples d'applications et des rubriques qui contiennent des instructions détaillées pour l'exécution de tâches courantes.

- [Référence générale &#40;le développement Office dans Visual Studio&#41;](general-reference-office-development-in-visual-studio.md)

 Fournit des liens vers des informations détaillées sur les assemblys PIA (Primary Interop Assembly) Office, les manifestes, les éléments d’interface utilisateur et les messages d’erreur.

- [Référence managée &#40;le développement Office dans Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md)

 Fournit des liens vers des informations sur les espaces de noms API et les types utilisés dans les projets Office qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Pour obtenir une documentation de référence des API sur les espaces de noms et les types utilisés dans les projets Office qui ciblent le .NET Framework 3,5, consultez la section de référence suivante dans la documentation de Visual Studio 2008 : [2007 référence gérée](managed-reference-office-development-in-visual-studio.md)par le système.

- [Informations de référence sur les API non managées &#40;le développement Office dans Visual Studio&#41;](unmanaged-api-reference-office-development-in-visual-studio.md)

 Contient des liens vers des informations sur les interfaces COM que vous pouvez utiliser pour effectuer des actions comme le chargement et le déchargement de compléments VSTO managés dans des applications Office.

## <a name="related-sections"></a>Sections connexes
- [Développement Office avec le portail des développeurs Visual Studio](https://developer.microsoft.com/office/docs) Fournit des ressources supplémentaires, telles que des articles techniques, des vidéos et des blogs.

- [Centre de développement Visual Studio](https://visualstudio.microsoft.com/) Fournit des ressources Visual Studio supplémentaires, telles que des articles techniques, des vidéos et des blogs.

- [Microsoft Office section développement de MSDN Library](/previous-versions/office/office-12/bb726434(v=office.12)) La zone de MSDN Library où vous pouvez trouver des articles et de la documentation de référence sur le développement de solutions pour plusieurs versions d’Office (non spécifiques au développement Office à l’aide de Visual Studio).

- [Développement d’applications dans Visual Studio](/previous-versions/h8w79z10(v=vs.140)) Contient des liens vers des rubriques qui expliquent comment vous pouvez utiliser Visual Studio pour concevoir, développer, déboguer et déployer des applications Web, des services Web XML et des applications clientes traditionnelles.

- [Programmation .NET Framework dans Visual Studio](/previous-versions/visualstudio/visual-studio-2010/k1s94fta(v=vs.100)) Décrit le développement d’applications avec le .NET Framework dans Visual Basic et Visual C#.
