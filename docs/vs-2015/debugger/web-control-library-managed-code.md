---
title: Bibliothèque de contrôles Web (code managé) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], Web control libraries
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031f894eb2e117a213f4f9fbbf08ac57a1512d61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688174"
---
# <a name="web-control-library-managed-code"></a>Bibliothèque de contrôles Web (code managé)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le modèle de projet de bibliothèque de contrôles Web permet de créer une DLL. Étant donné que la bibliothèque de classes est une DLL, vous ne pouvez pas l'exécuter directement. Vous devez créer une page [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] qui incorpore le contrôle. Pour plus d’informations, consultez [modèle de bibliothèque de contrôles Web](https://msdn.microsoft.com/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### <a name="to-debug-a-web-control-library-method-1"></a>Pour déboguer une bibliothèque de contrôles Web (Méthode 1)  
  
1. Ouvrez un projet de bibliothèque de contrôles Web existant ou créez-en un.  
  
2. Créez une page [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] qui incorpore le contrôle.  
  
3. Sur le site web qui héberge l’atelier de test [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], créez un sous-répertoire appelé `/Code`.  
  
4. Copiez le code source du contrôle dans le sous-répertoire `/Code`.  
  
5. Ouvrez le code source dans le sous-répertoire `/Code` et définissez des points d'arrêt.  
  
6. Ouvrez une fenêtre de navigateur avec une URL qui pointe sur l'atelier de test. Vous pouvez commencer à déboguer dès qu'un point d'arrêt dans le contrôle est atteint.  
  
### <a name="to-debug-a-web-control-library-method-2"></a>Pour déboguer une bibliothèque de contrôles Web (méthode 2)  
  
1. Créez le projet d'application hôte et le projet de contrôle Web dans la même solution.  
  
2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur l’application hôte et choisissez **Ajouter une référence**.  
  
3. Ajoutez une référence au projet de contrôle Web.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications Web ASP.NET](../debugger/debugging-preparation-aspnet-web-applications.md)
