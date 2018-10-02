---
title: Dépannage des extraits | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a6cc8cde833d9580e3fae03df2df11e87eed8cf2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506415"
---
# <a name="troubleshooting-snippets"></a>Dépannage des extraits
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [dépannage des extraits de code](https://docs.microsoft.com/visualstudio/ide/troubleshooting-snippets).  
  
Les problèmes liés aux extraits de code IntelliSense sont généralement provoqués pour deux raisons : un fichier d’extrait endommagé ou un fichier d’extrait avec du contenu incorrect.  
  
## <a name="common-problems"></a>Problèmes courants  
  
### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>L’extrait ne peut pas être déplacé de l’Explorateur de fichiers vers un fichier source Visual Studio  
  
-   Le code XML dans le fichier d’extrait est peut-être endommagé. L’**Éditeur XML** dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] peut identifier les problèmes dans la structure XML.  
  
-   Le fichier d’extrait n’est peut-être pas conforme au schéma d’extrait. L’**Éditeur XML** dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] peut identifier les problèmes dans la structure XML.  
  
### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Le code comporte des erreurs de compilateur qui ne sont pas mises en surbrillance  
  
-   Une référence de projet est peut-être manquante. Examinez la documentation relative à l’extrait. Si la référence n’est pas trouvée sur l’ordinateur, vous devez l’installer. Le fait d’insérer un extrait doit ajouter au projet toutes les références nécessaires. Si les informations de référence manquent dans l’extrait, vous pouvez signaler cette erreur au créateur de l’extrait.  
  
-   Une variable n’est peut-être pas définie. Les variables non définies dans un extrait doivent être mises en surbrillance. Si tel n’est pas le cas, vous pouvez signaler cette erreur au créateur de l’extrait.  
  
## <a name="see-also"></a>Voir aussi  
 [Extraits de code](../ide/code-snippets.md)



