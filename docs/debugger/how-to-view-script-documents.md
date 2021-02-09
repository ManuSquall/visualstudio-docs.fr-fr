---
title: Afficher les documents de script | Microsoft Docs
description: Découvrez comment afficher des documents de script JavaScript côté serveur dans Visual Studio à l’aide de Explorateur de solutions.
ms.custom: SEO-VS-2020
ms.date: 11/05/2019
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cfaa4e2558d8d1f102b0e442e9c509313f860e4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853096"
---
# <a name="how-to-view-script-documents-javascript"></a>Comment : afficher des documents de script (JavaScript)

Les fichiers de script côté serveur sont visibles dans Explorateur de solutions. Les fichiers de script côté client sont visibles uniquement lorsque vous êtes en mode débogage ou en mode arrêt. Les fichiers de script côté client apparaissent dans le nœud **documents de script** .

Pour certains types d’applications qui génèrent dynamiquement des pages, il est plus facile d’entrer en mode arrêt et de déboguer lorsque vous définissez un point d’arrêt à partir d’un document de script chargé dans le navigateur. De même, vous pouvez ajouter l' `debugger` instruction à partir d’un document de script chargé pour passer en mode arrêt. Cet article explique comment afficher ces documents.

> [!NOTE]
> Avant [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] , les fichiers de script côté client générés à partir du script côté serveur apparaissaient dans la fenêtre Explorateur de scripts.

### <a name="to-view-a-server-side-script-document"></a>Pour afficher un document de script côté serveur

1. Dans **Explorateur de solutions**, ouvrez le **\<Website Pathname>** nœud.

2. Double-cliquez sur le fichier de script que vous souhaitez afficher.

     Le fichier de script côté serveur s'ouvre dans une fenêtre source.

### <a name="to-view-a-client-side-script-document"></a>Pour afficher un document de script côté client

1. Dans l’**Explorateur de solutions**, ouvrez le nœud **Documents de script**.

2. Double-cliquez sur le fichier de script que vous souhaitez afficher.

     Le fichier de script côté client s'ouvre dans une fenêtre source.

## <a name="see-also"></a>Voir aussi
- [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)