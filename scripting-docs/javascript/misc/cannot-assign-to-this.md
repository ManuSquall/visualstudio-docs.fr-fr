---
title: Impossible d’assigner à’This' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8985c7201a8e315353dd89ab5e1f5a3ad3b403ea
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862774"
---
# <a name="cannot-assign-to-this"></a>Impossible d'affecter à 'this'
Vous avez tenté d’assigner une valeur à **ce**. **il** s’agit d’un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mot clé qui fait référence à :

- l’objet qui exécute actuellement une méthode,

- objet global s’il n’y a aucune méthode actuelle (ou si la méthode n’appartient à aucun autre objet).

Une méthode est une [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fonction qui est appelée par l’intermédiaire d’un objet. Dans une méthode, le mot clé **This** est une référence à l’objet à l’aide duquel la méthode a été appelée (qui devient l’objet créé en appelant le constructeur de classe avec l’opérateur **New** ).

À l’intérieur d’une méthode, vous pouvez **l’utiliser pour** faire référence à l’objet en cours, mais vous ne pouvez pas assigner une nouvelle valeur à **ce**.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- N’essayez pas d’assigner à **ce**. Pour accéder à une propriété ou à une méthode d’un objet instancié, utilisez l’opérateur point (par exemple, **Circle. RADIUS**).

  > [!NOTE]
  > Vous ne pouvez pas nommer une variable créée par **l'** utilisateur. Il s’agit d’un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mot réservé.

## <a name="see-also"></a>Voir aussi

- [Cette instruction](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/this)
- [Résolution des problèmes liés aux scripts](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)