---
title: 'Comment : ajouter un fichier de configuration d’application à un projet C# | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8417b5520dc9587fa3231a3bc459335d2a9896d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667535"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Comment : ajouter un fichier de configuration d'application à un projet C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En ajoutant un fichier de configuration d’application (fichier app.config) à un projet C#, vous pouvez personnaliser la façon dont le CLR (Common Language Runtime) localise et charge les fichiers d’assembly. Pour plus d’informations sur les fichiers de configuration de l’application, consultez [Comment le runtime localise les assemblys](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).

> [!NOTE]
> Le Windows Store ne prend pas en charge <xref:System.Configuration> . Par conséquent, les applications du Store ne contiennent pas de modèle de app.config.

 Quand vous générez votre projet, l’environnement de développement copie automatiquement votre fichier app.config, modifie le nom de fichier de la copie pour qu’il corresponde à votre fichier exécutable, puis déplace la copie dans le répertoire bin.

### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Pour ajouter un fichier de configuration d’application à votre projet C#

1. Dans la barre de menus, choisissez **projet**, **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s'affiche.

2. Développez **installé**, développez **éléments Visual C#**, puis choisissez le modèle **fichier de configuration** de l’application.

3. Dans la zone de texte **Nom**, entrez un nom, puis choisissez le bouton **Ajouter**.

     Un fichier nommé app.config est ajouté à votre projet.

## <a name="see-also"></a>Voir aussi
 [Gestion des paramètres d’application (.net)](../ide/managing-application-settings-dotnet.md) [schéma du fichier de configuration](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38) [Configuration des applications](https://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f) [Comment : configurer une application pour cibler une version de .NET Framework](https://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717) [à l’aide de l’environnement de développement Visual Studio pour C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)