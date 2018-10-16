---
title: 'Erreur : Pare-feu sur ordinateur Local | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cbca2e944e7313e54fd469dd41774f40931ee3d2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245347"
---
# <a name="error-firewall-on-local-machine"></a>Erreur : Pare-feu sur ordinateur local
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le pare-feu de connexion Internet sur l'ordinateur local, à partir duquel vous exécutez Visual Studio, n'est pas configuré pour autoriser le débogage distant. Pour le débogage distant managé ou natif avec le transport par défaut, le port TCP 135 doit être ouvert pour le trafic DCOM. Le partage de fichiers et d'imprimantes doit être ouvert, et devenv.exe doit être ajouté à la liste d'exceptions. L'ouverture de certains ports IPSEC peut également être nécessaire.  
  
 Pour plus d’informations, consultez [définir Up the Remote Tools sur l’appareil](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).



