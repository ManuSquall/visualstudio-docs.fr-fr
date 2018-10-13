---
title: Déploiement ClickOnce sur Windows Vista | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 6340d34e6f974cf8e7ea6f2dd7fea38b5ef94a57
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224508"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Déploiement ClickOnce sur Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Création d’applications dans Visual Studio pour le contrôle de compte d’utilisateur (UAC) sur Windows Vista génère normalement un manifeste incorporé, encodé binaires comme données XML dans le fichier exécutable de l’application. Étant donné que les applications ClickOnce and Registration-Free COM requièrent un manifeste externe, Visual Studio génère un fichier pour ces types de projets contenant les données de compte d’utilisateur au lieu d’un manifeste incorporé. Par défaut, Visual Studio utilise les informations à partir d’un fichier App .manifest pour générer les informations de manifeste de contrôle de compte utilisateur externes (pour le déploiement ClickOnce and Registration-Free COM), ou les incorporer dans le fichier exécutable de l’application (pour tous les autres cas). Visual Studio fournit les options suivantes pour la génération de manifeste :  
  
-   Utilisez un manifeste incorporé. Incorporer des données de contrôle de compte utilisateur dans le fichier exécutable de l’application et exécuter en tant qu’utilisateur normal.  
  
     Il s’agit du paramètre par défaut (sauf si vous utilisez ClickOnce). Ce paramètre prend en charge le fonctionnement habituel dans lequel Visual Studio sur Windows Vista ; Autrement dit, la génération d’un manifeste interne et externe, les deux à l’aide de `AsInvoker`.  
  
-   Utilisez un manifeste externe. Générez un manifeste externe à l’aide d’App.manifest.  
  
     Cela génère uniquement le manifeste externe en utilisant les informations dans App.manifest. Lorsque vous publiez une application à l’aide de ClickOnce ou COM sans inscription, Visual Studio ajoute App.manifest au projet et ajoute cette option.  
  
-   N’utilisez aucun manifeste. Créez l’application sans manifeste.  
  
     Cette approche est également appelé *virtualisation*. Utilisez cette option pour la compatibilité avec les applications existantes à partir de versions antérieures de Visual Studio.  
  
 Les nouvelles propriétés sont disponibles sur le **Application** page du Concepteur de projet (pour les projets Visual c# uniquement) et dans le format de fichier projet MSBuild.  
  
 Notez que la méthode de configuration de génération de manifeste de contrôle de compte utilisateur dans l’IDE Visual Studio diffère selon le type de projet (Visual c# et Visual Basic).  
  
 Pour plus d’informations sur la configuration des projets Visual c# pour la génération de manifeste, consultez [Page Application, Concepteur de projets (c#)](../ide/reference/application-page-project-designer-csharp.md).  
  
 Pour plus d’informations sur la configuration des projets Visual Basic pour la génération de manifeste, consultez [Page Application, Concepteur de projets (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Autorisations utilisateur et Visual Studio](http://msdn.microsoft.com/en-us/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Page Application, Concepteur de projets (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Page Application, Concepteur de projets (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)



