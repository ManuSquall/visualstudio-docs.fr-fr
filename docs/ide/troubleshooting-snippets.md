---
title: Dépannage des extraits
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd0151ff22146d745c42204ec66b9f5d35c2c8b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshooting-snippets"></a>Dépannage des extraits

Les problèmes liés aux extraits de code IntelliSense sont généralement provoqués pour deux raisons : un fichier d’extrait endommagé ou un fichier d’extrait avec du contenu incorrect.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>L’extrait ne peut pas être déplacé de l’Explorateur de fichiers vers un fichier source Visual Studio

-   Le code XML dans le fichier d’extrait est peut-être endommagé. L’**Éditeur XML** dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] peut identifier les problèmes dans la structure XML.

-   Le fichier d’extrait n’est peut-être pas conforme au schéma d’extrait. L’**Éditeur XML** dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] peut identifier les problèmes dans la structure XML.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Le code comporte des erreurs de compilateur qui ne sont pas mises en surbrillance

-   Une référence de projet est peut-être manquante. Examinez la documentation relative à l’extrait. Si la référence n’est pas trouvée sur l’ordinateur, vous devez l’installer. Le fait d’insérer un extrait doit ajouter au projet toutes les références nécessaires. Si les informations de référence manquent dans l’extrait, vous pouvez signaler cette erreur au créateur de l’extrait.

-   Une variable n’est peut-être pas définie. Les variables non définies dans un extrait doivent être mises en surbrillance. Si tel n’est pas le cas, vous pouvez signaler cette erreur au créateur de l’extrait.

## <a name="see-also"></a>Voir aussi

- [Extraits de code](../ide/code-snippets.md)