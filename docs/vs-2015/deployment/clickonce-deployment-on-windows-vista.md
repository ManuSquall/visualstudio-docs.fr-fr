---
title: Déploiement ClickOnce sur Windows Vista | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e25f9da960b1de8acb1950b2bdd3ab7e61409f17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675476"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Déploiement ClickOnce sur Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La génération d’applications dans Visual Studio pour le contrôle de compte d’utilisateur (UAC) sur Windows Vista génère normalement un manifeste incorporé, encodé en tant que données XML binaires dans le fichier exécutable de l’application. Étant donné que ClickOnce et les applications COM sans inscription requièrent un manifeste externe, Visual Studio génère un fichier pour ces types de projets contenant les données UAC au lieu d’un manifeste incorporé. Par défaut, Visual Studio utilise les informations d’un fichier appelé App. manifest pour générer des informations de manifeste de contrôle de compte d’utilisateur externes (pour ClickOnce et un déploiement COM sans inscription), ou pour l’incorporer dans le fichier exécutable de l’application (pour tous les autres cas). Visual Studio fournit les options suivantes pour la génération de manifeste :  
  
- Utilisez un manifeste incorporé. Incorporez les données UAC dans le fichier exécutable de l’application et exécutez-les en tant qu’utilisateur normal.  
  
   Il s’agit du paramètre par défaut (sauf si vous utilisez ClickOnce). Ce paramètre prend en charge la méthode habituelle de fonctionnement de Visual Studio sur Windows Vista. autrement dit, la génération d’un manifeste interne et externe, à l’aide de `AsInvoker` .  
  
- Utilisez un manifeste externe. Générez un manifeste externe à l’aide d’App. manifest.  
  
   Cela génère uniquement le manifeste externe à l’aide des informations contenues dans App. manifest. Quand vous publiez une application à l’aide de ClickOnce ou de COM sans inscription, Visual Studio ajoute App. manifest au projet et ajoute cette option.  
  
- N’utilisez aucun manifeste. Créez l’application sans manifeste.  
  
   Cette approche est également appelée *virtualisation*. Utilisez cette option pour la compatibilité avec les applications existantes des versions antérieures de Visual Studio.  
  
  Les nouvelles propriétés sont disponibles dans la page **application** du concepteur de projet (pour les projets Visual C# uniquement) et dans le format de fichier projet MSBuild.  
  
  Notez que la méthode de configuration de la génération de manifeste de contrôle de compte d’utilisateur dans l’IDE de Visual Studio diffère selon le type de projet (Visual C# et Visual Basic).  
  
  Pour plus d’informations sur la configuration de projets Visual C# pour la génération de manifestes, consultez [page application, concepteur de projets (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  Pour plus d’informations sur la configuration de projets Visual Basic pour la génération de manifestes, consultez [page application, concepteur de projets (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Autorisations utilisateur et Visual Studio](https://msdn.microsoft.com/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Page application, concepteur de projets (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Page Application, Concepteur de projet (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
