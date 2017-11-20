---
title: "Comment : ajouter un fichier de Configuration d’Application à un projet c# | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords: app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 097e7a2eac78fe85b2a3ab62d5cdf1fd18908d56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Comment : ajouter un fichier de configuration d'application à un projet C#
En ajoutant un fichier de configuration d’application (fichier app.config) à un projet c#, vous pouvez personnaliser la façon dont le common language runtime localise et charge les fichiers d’assembly. Pour plus d’informations sur les fichiers de configuration d’application, consultez [méthode de localisation des assemblys par le Runtime](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).  
  
> [!NOTE]
>  Les applications UWP ne contiennent pas un modèle de fichier app.config.
  
 Lorsque vous générez votre projet, l’environnement de développement copie automatiquement votre fichier app.config, modifie le nom de fichier de la copie pour correspondre à votre fichier exécutable, puis déplace la copie vers le répertoire bin.  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Pour ajouter un fichier de configuration d’application à votre projet c#  
  
1.  Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s’affiche.  
  
2.  Développez **installé**, développez **éléments Visual c#**, puis choisissez le **fichier de Configuration d’Application** modèle.  
  
3.  Dans le **nom** zone de texte, entrez un nom, puis choisissez le **ajouter** bouton.  
  
     Un fichier nommé app.config est ajouté à votre projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des paramètres d’application (.NET)](../ide/managing-application-settings-dotnet.md)   
 [Schéma des fichiers de configuration](/dotnet/framework/configure-apps/file-schema/index)   
 [Configuration d’applications](/dotnet/framework/configure-apps/index)   
 [Comment : configurer une application pour cibler une Version du .NET Framework](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Utilisation de l’environnement de développement Visual Studio pour C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)