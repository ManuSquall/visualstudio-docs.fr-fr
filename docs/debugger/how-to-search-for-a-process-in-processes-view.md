---
title: Rechercher un processus dans la vue processus | Microsoft Docs
description: Recherchez un processus spécifique dans la vue processus de l’outil Spy + + en utilisant son ID de processus ou sa chaîne de module comme critère de recherche lors du débogage dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85b2c2bab29316846620c7dbec935b41eec1d9df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845072"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Comment : rechercher un processus dans la vue Processus
Vous pouvez rechercher un processus spécifique dans la vue processus en utilisant son ID de processus ou sa chaîne de module comme critère de recherche. Vous pouvez également spécifier le sens initial de la recherche. Les champs de la boîte de dialogue affichent les attributs du processus sélectionné dans l’arborescence des processus.

### <a name="to-search-for-a-process-in-processes-view"></a>Pour rechercher un processus dans la vue processus

1. Réorganisez vos fenêtres afin que Spy + + et une fenêtre d' [affichage des processus](../debugger/processes-view.md) actifs soient visibles.

2. Dans le menu **Rechercher** , choisissez **Rechercher le processus** .

    La [boîte de dialogue recherche de processus](../debugger/process-search-dialog-box.md) s’ouvre.

3. Tapez l’ID de processus ou une chaîne de module en tant que critères de recherche.

4. Effacez tous les champs pour lesquels vous ne souhaitez pas spécifier de valeurs.

   > [!TIP]
   > Pour rechercher tous les processus détenus par un module, décochez la case **traiter** et tapez le nom du module dans la zone **module** . Ensuite, utilisez **Rechercher suivant** pour poursuivre la recherche des processus.

5. Choisissez **haut** ou **bas** pour la direction initiale de la recherche.

6. Cliquez sur **OK**.

   Si un processus de correspondance est trouvé, il est mis en surbrillance dans la fenêtre **vue processus** .