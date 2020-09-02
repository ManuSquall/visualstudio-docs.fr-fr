---
title: 'Comment : spécifier une version de .NET Framework pour le débogage | Microsoft Docs'
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
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4c785c419ead31ad90e2b20ae7f48af778598bb6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176556"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Comment : spécifier une version .NET Framework pour le débogage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogueur [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] prend en charge le débogage des versions antérieures ainsi que de la version actuelle de Microsoft [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Si vous démarrez une application à partir de Visual Studio, le débogueur identifie toujours la version correcte du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] pour l’application que vous déboguez. Si l’application est déjà en cours d’exécution et que vous utilisez l' **attachement à**, le débogueur peut ne pas toujours être en mesure d’identifier une version antérieure du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Si cela se produit, un message d'erreur s'affiche qui indique,  
  
 Le débogueur a évalué de façon incorrecte la version du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que votre application va utiliser.  
  
 Dans ces cas rares, vous pouvez définir une clé de Registre pour indiquer au débogueur la version à utiliser.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Pour spécifier une version .NET Framework pour le débogage  
  
1. Recherchez dans le répertoire Windows\Microsoft.NET\Framework les versions du .NET Framework installées sur votre ordinateur. Les numéros de version sont similaires à ceci :  
  
     `V1.1.4322`  
  
     Identifiez le numéro de version correct et prenez-en note.  
  
2. Démarrez l’**Éditeur du Registre** (regedit).  
  
3. Dans l’**Éditeur du Registre**, ouvrez le dossier HKEY_LOCAL_MACHINE.  
  
4. Accédez à : HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Si la clé n’existe pas, cliquez avec le bouton droit sur HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine, puis cliquez sur **Nouvelle clé**. Nommez la nouvelle clé `{449EC4CC-30D2-4032-9256-EE18EB41B62B}` .  
  
5. Après avoir accédé à {449EC4CC-30D2-4032-9256-EE18EB41B62B}, recherchez la clé CLRVersionForDebugging dans la colonne **Nom**.  
  
    1. Si la clé n’existe pas, cliquez avec le bouton droit sur {449EC4CC-30D2-4032-9256-EE18EB41B62B}, puis cliquez sur **Nouvelle valeur de chaîne**. Cliquez ensuite avec le bouton droit sur la nouvelle valeur de chaîne, cliquez sur **Renommer**et tapez `CLRVersionForDebugging` .  
  
6. Double-cliquez sur **CLRVersionForDebugging**.  
  
7. Dans la zone **Modification de la chaîne**, tapez le numéro de version du .NET Framework dans la zone **Valeur**. Par exemple : V1.1.4322  
  
8. Cliquez sur **OK**.  
  
9. Fermez l' **éditeur du Registre**.  
  
     Si vous obtenez encore un message d'erreur lorsque vous commencez à déboguer, vérifiez que vous avez entré correctement le numéro de version dans le Registre. Assurez-vous également que la version du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que vous utilisez est prise en charge par Visual Studio. Le débogueur est compatible avec la version actuelle et les versions antérieures du .NET Framework, mais il n'offre peut-être pas une compatibilité ascendante avec les futures versions.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)
