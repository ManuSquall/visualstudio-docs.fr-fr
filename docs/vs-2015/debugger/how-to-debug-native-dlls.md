---
title: 'Comment : déboguer des DLL natives | Microsoft Docs'
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
ms.openlocfilehash: 16a533b27e619526edab71374d922e68baf0a4b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702677"
---
# <a name="how-to-debug-native-dlls"></a>Comment : déboguer des DLL natives
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Lorsque vous déboguez une DLL, vous pouvez commencer le débogage à partir :  
  
- du projet utilisé pour créer l'exécutable qui appelle la DLL ;  
  
  \- ou -  
  
- du projet utilisé pour créer la DLL.  
  
  Si vous disposez du projet utilisé pour créer l'exécutable, démarrez le débogage à partir de ce projet. Vous pouvez ensuite ouvrir un fichier source pour la DLL et définir les points d'arrêt dans ce fichier, même s'il ne fait pas partie du projet utilisé pour créer l'exécutable. Pour plus d’informations, consultez [Points d’arrêt](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
  Si vous démarrez le débogage à partir du projet qui crée la DLL, vous devez spécifier l'exécutable que vous voulez utiliser dans le débogage de la DLL.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>Pour spécifier un exécutable pour la session de débogage  
  
1. Dans **Explorateur de solutions**, sélectionnez le projet qui crée la dll.  
  
2. Dans le menu **affichage** , cliquez sur**pages de propriétés**.  
  
3. Dans la boîte de dialogue **pages de propriétés** , ouvrez le dossier **Propriétés de configuration** et sélectionnez la catégorie **débogage** .  
  
4. Dans la zone **commande** , spécifiez le nom du chemin d’accès du conteneur. Par exemple, C:\Program Files\MyApplication\MYAPP.EXE.  
  
5. Dans la zone arguments de la **commande** , spécifiez les arguments nécessaires pour l’exécutable.  
  
   Si vous ne spécifiez pas le fichier exécutable dans la boîte de dialogue**pages de propriétés** du _projet_, la [boîte de dialogue exécutable pour la session de débogage](../debugger/executable-for-debugging-session-dialog-box.md) s’affiche lorsque vous démarrez le débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)
