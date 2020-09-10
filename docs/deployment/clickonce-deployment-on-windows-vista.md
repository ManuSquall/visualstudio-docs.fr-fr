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
ms.openlocfilehash: 8b76804eb8c06acbcdeac017108773056ee38338
ms.sourcegitcommit: 1803a67b516f67b209d8f4cf147314e604ef1927
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89641488"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Déploiement ClickOnce sur Windows Vista

La génération d’applications dans Visual Studio pour le contrôle de compte d’utilisateur (UAC) sur Windows Vista génère normalement un manifeste incorporé, encodé en tant que données XML binaires dans le fichier exécutable de l’application.  ClickOnce et les applications COM sans inscription requièrent un manifeste externe, de sorte que Visual Studio génère un fichier pour ces projets contenant les données UAC au lieu d’un manifeste incorporé. Pour ClickOnce et les déploiements COM sans inscription, Visual Studio utilise les informations d’un fichier appelé *app. manifest* pour générer des informations de manifeste de contrôle de compte d’utilisateur externes. Dans tous les autres cas, Visual Studio incorpore les données du contrôle de compte d’utilisateur dans le fichier exécutable de l’application.

Visual Studio fournit les options suivantes pour la génération de manifeste :

- Utilisez un manifeste incorporé. Incorporez les données UAC dans le fichier exécutable de l’application et exécutez-les en tant qu’utilisateur normal.

   Il s’agit du paramètre par défaut (sauf si vous utilisez ClickOnce). Ce paramètre prend en charge la méthode habituelle de fonctionnement de Visual Studio sur Windows Vista, avec la génération d’un manifeste interne et externe à l’aide de `AsInvoker` .

- Utilisez un manifeste externe. Générez un manifeste externe à l’aide d' *app. manifest*.

   Cela génère uniquement le manifeste externe à l’aide des informations contenues dans *app. manifest*. Quand vous publiez une application à l’aide de ClickOnce ou de COM sans inscription, Visual Studio ajoute *app. manifest* au projet, puis ajoute cette option.

- N’utilisez aucun manifeste. Créez l’application sans manifeste.

   Cette approche est également appelée *virtualisation*. Utilisez cette option pour la compatibilité avec les applications existantes des versions antérieures de Visual Studio.

  Les nouvelles propriétés sont disponibles dans la page **application** du concepteur de projet (pour les projets Visual C# uniquement) et dans le format de fichier projet MSBuild.

  La méthode de configuration de la génération de manifeste de contrôle de compte d’utilisateur dans l’IDE de Visual Studio diffère selon le type de projet (Visual C# ou Visual Basic).

  * Pour plus d’informations sur la configuration de projets Visual C# pour la génération de manifestes, consultez [page application, concepteur de projets (C#)](../ide/reference/application-page-project-designer-csharp.md).

  * Pour plus d’informations sur la configuration de projets Visual Basic pour la génération de manifestes, consultez [page application, concepteur de projets (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

## <a name="see-also"></a>Voir aussi
- [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Autorisations utilisateur et Visual Studio](/previous-versions/ms165100(v=vs.100))
- [Page Application, Concepteur de projet (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Page Application, Concepteur de projet (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)