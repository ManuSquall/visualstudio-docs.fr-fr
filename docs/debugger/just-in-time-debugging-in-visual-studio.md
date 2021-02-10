---
title: Désactiver le débogueur juste-à-temps | Microsoft Docs
description: La boîte de dialogue débogueur juste-à-temps peut s’ouvrir lorsqu’une erreur se produit dans une application. Découvrez ce que vous pouvez faire quand cela se produit et comment l’éviter.
ms.custom: SEO-VS-2020
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 670809ea2c9ef04107dbec5634f40831b68b94c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931498"
---
# <a name="disable-the-just-in-time-debugger"></a>Désactiver le débogueur juste-à-temps

La boîte de dialogue débogueur juste-à-temps peut s’ouvrir lorsqu’une erreur se produit dans une application en cours d’exécution et empêcher l’application de se poursuivre.

Le débogueur juste-à-temps vous donne la possibilité de lancer Visual Studio pour déboguer l’erreur. Vous devez avoir installé Visual Studio ou un autre débogueur sélectionné pour afficher des informations détaillées sur l’erreur ou essayer de la déboguer.

Si vous êtes déjà un utilisateur de Visual Studio et que vous souhaitez essayer de déboguer l’erreur, consultez [Déboguer à l’aide du débogueur juste-à-temps](../debugger/debug-using-the-just-in-time-debugger.md). Si vous ne pouvez pas corriger l’erreur ou si vous souhaitez empêcher l’ouverture du débogueur juste-à-temps, vous pouvez [désactiver le débogage juste-à-temps à partir de Visual Studio](debug-using-the-just-in-time-debugger.md#BKMK_Enabling).

Si vous aviez installé Visual Studio, mais que vous n’en avez plus, vous devrez peut-être [désactiver le débogage juste-à-temps à partir du Registre Windows](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry).

Si vous n’avez pas installé Visual Studio, vous pouvez empêcher le débogage juste-à-temps en désactivant le débogage de script ou le débogage côté serveur.

- Si vous essayez d’exécuter une application Web, désactivez le débogage de script :

  Dans **le panneau de configuration** Windows  >    >  **Options Internet** et Internet, sélectionnez **désactiver le débogage de script (Internet Explorer)** et **désactivez le débogage de script (autre)**. Les étapes et les paramètres exacts dépendent de votre version de Windows et de votre navigateur.

  ![Options Internet JIT](../debugger/media/jitinternetoptions.png "Options Internet JIT")

- Si vous hébergez une application Web ASP.NET dans IIS, désactivez le débogage côté serveur :

  1. Dans l' **affichage fonctionnalités** du gestionnaire des services Internet, sous la section **ASP.net** , double-cliquez sur **compilation .net**, ou sélectionnez-la, puis sélectionnez **ouvrir la fonctionnalité** dans le volet **actions** .
  1. Sous **comportement**  >  **Debug**, sélectionnez **false**. Les étapes sont différentes dans les versions antérieures d’IIS.

Une fois que vous avez désactivé le débogage juste-à-temps, l’application peut être en mesure de gérer l’erreur et de s’exécuter normalement.

Si l’application a toujours une erreur non gérée, vous pouvez voir un message d’erreur ou l’application peut se bloquer ou cesser de répondre. L’application ne s’exécute pas normalement tant que l’erreur n’est pas corrigée. Vous pouvez essayer de contacter le propriétaire de l’application et de lui demander de le résoudre.
