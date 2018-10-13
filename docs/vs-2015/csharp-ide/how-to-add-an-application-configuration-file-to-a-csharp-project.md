---
title: 'Comment : ajouter un fichier de Configuration d’Application à un projet c# | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 43245704a2393b298f0f1d948d8a8829a4ef9bc4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204787"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Comment : ajouter un fichier de configuration d'application à un projet C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En ajoutant un fichier de configuration d’application (fichier app.config) à un projet C#, vous pouvez personnaliser la façon dont le CLR (Common Language Runtime) localise et charge les fichiers d’assembly. Pour plus d’informations sur les fichiers de configuration d’application, consultez [méthode de localisation des assemblys par le Runtime](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).  
  
> [!NOTE]
>  Le Windows Store ne prend pas en charge <xref:System.Configuration>. Par conséquent, les applications de Store ne contiennent pas un modèle de fichier app.config.  
  
 Lorsque vous générez votre projet, l’environnement de développement copie automatiquement votre fichier app.config, modifie le nom de fichier de la copie pour correspondre à votre fichier exécutable, puis déplace la copie dans le répertoire bin.  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Pour ajouter un fichier de configuration d’application à votre projet c#  
  
1.  Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s’affiche.  
  
2.  Développez **installé**, développez **éléments Visual c#**, puis choisissez le **fichier de Configuration d’Application** modèle.  
  
3.  Dans la zone de texte **Nom**, entrez un nom, puis choisissez le bouton **Ajouter**.  
  
     Un fichier nommé app.config est ajouté à votre projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des paramètres d’application (.NET)](../ide/managing-application-settings-dotnet.md)   
 [Schéma des fichiers de configuration](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [Configuration d’applications](http://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f)   
 [Comment : configurer une application pour cibler une Version du .NET Framework](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Utilisation de l’environnement de développement Visual Studio pour C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)