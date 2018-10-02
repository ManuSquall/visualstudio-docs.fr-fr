---
title: 'Erreur : Pare-feu sur ordinateur Local | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 6f4cee2d391038c9157666078c6fd83027bc35e6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508797"
---
# <a name="error-firewall-on-local-machine"></a>Erreur : Pare-feu sur ordinateur local
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [erreur : pare-feu sur ordinateur Local](https://docs.microsoft.com/visualstudio/debugger/error-firewall-on-local-machine).  
  
Le pare-feu de connexion Internet sur l'ordinateur local, à partir duquel vous exécutez Visual Studio, n'est pas configuré pour autoriser le débogage distant. Pour le débogage distant managé ou natif avec le transport par défaut, le port TCP 135 doit être ouvert pour le trafic DCOM. Le partage de fichiers et d'imprimantes doit être ouvert, et devenv.exe doit être ajouté à la liste d'exceptions. L'ouverture de certains ports IPSEC peut également être nécessaire.  
  
 Pour plus d’informations, consultez [définir Up the Remote Tools sur l’appareil](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).



