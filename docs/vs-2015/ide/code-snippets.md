---
title: Extraits de code | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- code snippets, replacement parameters
- code snippets, surround with
- replacement parameters
- code snippets, expansion
- surround with
- code snippets
ms.assetid: 85976ad9-4c9a-4e7b-896e-66ec6f955199
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 29087da38fe7c89936e3823b43e591116396e432
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47492793"
---
# <a name="code-snippets"></a>Extraits de code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [extraits de Code](https://docs.microsoft.com/visualstudio/ide/code-snippets).  
  
Les extraits de code sont de petits blocs de code réutilisables que vous pouvez insérer dans un fichier de code à l'aide d'une commande de menu contextuel ou une combinaison de touches d'accès rapide. Ils contiennent généralement des blocs de code fréquemment utilisés tels que les blocs try-finally ou if-else, mais ils permettent d'insérer des classes ou des méthodes entières.  
  
## <a name="expansion-snippets-and-surround-with-snippets"></a>Extraits de code d'extension et extraits de code d'encerclement  
 Dans Visual Studio, il existe deux types d'extrait de code : les extraits d'extension, qui sont ajoutés à un point d'insertion spécifié et qui peuvent remplacer un raccourci d'extrait de code, et les extraits de code d'encerclement (C# et C++ uniquement), qui sont ajoutés autour d'un bloc de code sélectionné.  
  
 Exemple d'extrait de code d'insertion : en C#, le raccourci tryf est utilisé pour insérer un bloc try-finally :  
  
```  
try  
{  
  
}  
finally  
{  
  
}  
  
```  
  
 Pour insérer cet extrait, cliquez sur **Insérer un extrait** dans le menu contextuel de la fenêtre de code, cliquez sur **Visual C#**, tapez `tryf`, puis appuyez sur la touche TAB. Vous pouvez également taper `tryf`, puis appuyer sur TAB + TAB.  
  
 Exemple d'extrait de code d'encerclement : en C++, le raccourci `if` peut être utilisé comme un extrait d'insertion ou comme un extrait de code d'encerclement. Si vous sélectionnez une ligne de code (par exemple `return FALSE;`), et que vous cliquez ensuite sur **Entourer de**, puis sur **if**, l’extrait est développé autour de la ligne :  
  
```  
if (true)  
{  
    return FALSE;  
}  
  
```  
  
## <a name="snippet-replacement-parameters"></a>Paramètres de remplacement d'extrait de code  
 Les extraits de code peuvent contenir des paramètres de remplacement, qui sont des espaces réservés que vous devez remplacer en fonction du code précis que vous écrivez. Dans l'exemple précédent, `true` est un paramètre de remplacement, que vous pouvez remplacer par la condition appropriée. Cette condition que vous apportez est répétée pour chaque instance du même paramètre de remplacement dans l'extrait de code.  
  
 Par exemple, en Visual Basic, un extrait de code insère une propriété. Cliquez sur **Insérer un extrait** dans le menu contextuel de la fenêtre de code, puis sur **Modèles de code**, sur **Propriétés, procédures, événements**, et enfin sur Définir une propriété. Le code suivant est inséré :  
  
```  
Private newPropertyValue As String  
Public Property NewProperty() As String  
    Get  
        Return newPropertyValue  
    End Get  
    Set(ByVal value As String)  
        newPropertyValue = value  
    End Set  
End Property  
  
```  
  
 Si vous remplacez `newPropertyValue` par `m_property`, chaque instance de `newPropertyValue` est modifiée. Si vous remplacez `String` par `Int` dans la déclaration de propriété, la valeur de la méthode set est également remplacée par `Int`.  
  
## <a name="code-snippet-manager"></a>Gestionnaire des extraits de code  
 Vous pouvez voir tous les extraits de code qui sont actuellement installés, ainsi que leur emplacement sur le disque, en cliquant sur **Outils/Gestionnaire des extraits de code**. Les extraits de code sont affichés par langage.  
  
 Vous pouvez ajouter et supprimer des répertoires d’extraits de code à l’aide des boutons **Ajouter** et **Supprimer** dans la boîte de dialogue **Gestionnaire des extraits de code**. Pour ajouter des extraits de code individuels, utilisez le bouton **Importer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : création d’un extrait de code](../ide/walkthrough-creating-a-code-snippet.md)   
 [Guide pratique pour distribuer des extraits de code](../ide/how-to-distribute-code-snippets.md)   
 [Bonnes pratiques pour l’utilisation des extraits de code](../ide/best-practices-for-using-code-snippets.md)   
 [Dépannage des extraits](../ide/troubleshooting-snippets.md)   
 [Extraits de code Visual C#](../ide/visual-csharp-code-snippets.md)   
 [Extraits de code Visual C++](../ide/visual-cpp-code-snippets.md)   
 [Référence de schéma des extraits de code](../ide/code-snippets-schema-reference.md)



