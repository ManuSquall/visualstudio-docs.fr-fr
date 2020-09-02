---
title: Contrôle d’exécution et évaluation d’État | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6476c925f37d70ab45bae129a8b8a379ee519c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152771"
---
# <a name="execution-control-and-state-evaluation"></a>Contrôle de l’exécution et évaluation de l’état
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le débogage d’une application nécessite l’implémentation de fonctionnalités de contrôle d’exécution telles que l’exécution pas à pas des fonctions, l’arrêt des points d’arrêt et la poursuite de l’exécution. Le débogage de Visual Studio base son contrôle d’exécution sur les événements envoyés entre les composants du débogueur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Contrôle du programme](../../extensibility/debugger/program-control.md)  
 Répertorie les routines suivantes qui se produisent au niveau du programme : définition de l’instruction suivante, exécution, exécution pas à pas, poursuite, interruption et reprise.  
  
 [Méthodes liées au point d’arrêt](../../extensibility/debugger/breakpoint-related-methods.md)  
 Définit les types de points d’arrêt liés et en attente que Visual Studio prend en charge.  
  
 [Évaluation de la pile des appels](../../extensibility/debugger/call-stack-evaluation.md)  
 Traite de l’implémentation des méthodes qui permettent d’afficher les frames de pile de la pile des appels en mode arrêt.  
  
 [Évaluation d’expression](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Explique comment le moteur de débogage (DE), l’évaluation d’expression (EE) et le gestionnaire de débogage de session sont impliqués dans l’analyse et l’évaluation d’une expression entrée dans l’une des fenêtres de l’IDE.  
  
 [Événements de contrôle](../../extensibility/debugger/control-events.md)  
 Présente l’interface utilisée pour envoyer des événements pendant l’exécution contrôlée du programme.
