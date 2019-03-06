---
title: Déploiement ClickOnce sur Windows Vista | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4beefddd429384fadda71d9742e8c0fac606c38e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56600101"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Déploiement ClickOnce sur Windows Vista

Création d’applications dans Visual Studio pour le contrôle de compte d’utilisateur (UAC) sur Windows Vista génère normalement un manifeste incorporé, encodé binaires comme données XML dans le fichier exécutable de l’application.  Les applications ClickOnce et COM sans inscription requièrent un manifeste externe, afin de Visual Studio génère un fichier pour ces projets contenant les données de compte d’utilisateur au lieu d’un manifeste incorporé. Pour les déploiements ClickOnce and Registration-Free COM, Visual Studio utilise les informations à partir d’un fichier appelé *App.manifest* pour générer les informations de manifeste de contrôle de compte utilisateur externe. Pour tous les autres cas, Visual Studio incorpore les données de contrôle de compte utilisateur dans le fichier exécutable de l’application.

Visual Studio fournit les options suivantes pour la génération de manifeste :

- Utilisez un manifeste incorporé. Incorporer des données de contrôle de compte utilisateur dans le fichier exécutable de l’application et exécuter en tant qu’utilisateur normal.

   Il s’agit du paramètre par défaut (sauf si vous utilisez ClickOnce). Ce paramètre prend en charge le fonctionnement habituel dans lequel Visual Studio sur Windows Vista, avec la génération d’une commande interne et une externe manifeste à l’aide de `AsInvoker`.

- Utilisez un manifeste externe. Générez un manifeste externe à l’aide de *App.manifest*.

   Cela génère uniquement le manifeste externe en utilisant les informations dans *App.manifest*. Lorsque vous publiez une application à l’aide de ClickOnce ou COM sans inscription, Visual Studio ajoute *App.manifest* au projet, puis ajoute cette option.

- N’utilisez aucun manifeste. Créez l’application sans manifeste.

   Cette approche est également appelé *virtualisation*. Utilisez cette option pour la compatibilité avec les applications existantes à partir de versions antérieures de Visual Studio.

  Les nouvelles propriétés sont disponibles sur le **Application** page du Concepteur de projet (pour Visual C# projets uniquement) et dans le format de fichier projet MSBuild.

  La méthode de configuration de génération de manifeste de contrôle de compte utilisateur dans l’IDE Visual Studio diffère selon le type de projet (Visual C# ou Visual Basic).

  * Pour plus d’informations sur la configuration Visual C# projets pour la génération de manifeste, consultez [Application Page, Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md).

  * Pour plus d’informations sur la configuration des projets Visual Basic pour la génération de manifeste, consultez [Page Application, Concepteur de projets (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

## <a name="see-also"></a>Voir aussi
- [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Autorisations utilisateur et Visual Studio](https://msdn.microsoft.com/library/d5c55084-1e7b-4b61-b478-137db01c0fc0)
- [Page Application, Concepteur de projets (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Page Application, Concepteur de projets (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)