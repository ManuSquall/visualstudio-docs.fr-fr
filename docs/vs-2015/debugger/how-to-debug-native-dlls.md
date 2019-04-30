---
title: 'Procédure : Déboguer des DLL natives | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- DLLs, debugging
- executable files, specifying for debug sessions
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea2f40119425cc558b5486a9085b92b05ba81c97
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426522"
---
# <a name="how-to-debug-native-dlls"></a>Procédure : Déboguer des DLL natives
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Lorsque vous déboguez une DLL, vous pouvez commencer le débogage à partir :  
  
- du projet utilisé pour créer l'exécutable qui appelle la DLL ;  
  
  \- ou -  
  
- du projet utilisé pour créer la DLL.  
  
  Si vous disposez du projet utilisé pour créer l'exécutable, démarrez le débogage à partir de ce projet. Vous pouvez ensuite ouvrir un fichier source pour la DLL et définir les points d'arrêt dans ce fichier, même s'il ne fait pas partie du projet utilisé pour créer l'exécutable. Pour plus d’informations, consultez [Points d’arrêt](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
  Si vous démarrez le débogage à partir du projet qui crée la DLL, vous devez spécifier l'exécutable que vous voulez utiliser dans le débogage de la DLL.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>Pour spécifier un exécutable pour la session de débogage  
  
1. Dans **l’Explorateur de solutions**, sélectionnez le projet qui crée la DLL.  
  
2. À partir de la **vue** menu, choisissez**Pages de propriétés**.  
  
3. Dans le **Pages de propriétés** boîte de dialogue, ouvrez le **propriétés de Configuration** dossier et sélectionnez le **débogage** catégorie.  
  
4. Dans le **commande** , spécifiez le nom de chemin d’accès pour le conteneur. Par exemple, C:\Program Files\MyApplication\MYAPP.EXE.  
  
5. Dans le **Arguments de commande** , spécifiez les arguments nécessaires pour le fichier exécutable.  
  
   Si vous ne spécifiez pas l’exécutable dans le _projet_**Pages de propriétés** boîte de dialogue, le [exécutable pour la boîte de dialogue de Session de débogage](../debugger/executable-for-debugging-session-dialog-box.md) s’affiche lorsque vous démarrez le débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)
