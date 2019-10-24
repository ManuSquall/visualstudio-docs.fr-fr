---
title: Interface de l’Assistant (IDTWizard) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f571fbd0a68ddbf56b637071ac250159461f61d1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721530"
---
# <a name="wizard-interface-idtwizard"></a>Interface de l’Assistant (IDTWizard)
L’environnement de développement intégré (IDE) utilise l’interface <xref:EnvDTE.IDTWizard> pour communiquer avec les assistants. Les assistants doivent implémenter cette interface pour être installés dans l’IDE.

 La méthode <xref:EnvDTE.IDTWizard.Execute%2A> est la seule méthode associée à l’interface <xref:EnvDTE.IDTWizard>. Les assistants implémentent cette méthode et l’IDE appelle la méthode sur l’interface. L’exemple suivant illustre la signature de la méthode.

```
/* IDTWizard Method */
STDMETHOD(Execute)(THIS_
   /* [in] */ IDispatch *Application,
   /* [in] */ long hwndOwner,
   /* [in] */ SAFEARRAY * *ContextParams,
   /* [in] */ SAFEARRAY * *CustomParams,
   /* [out] [in] */ wizardResult *RetVal
   );
```

 Le mécanisme de démarrage est similaire pour les assistants **nouveau projet** et **Ajouter un nouvel élément** . Pour démarrer l’un ou l’autre, vous appelez l’interface <xref:EnvDTE.IDTWizard> définie dans Dteinternal. h. La seule différence est l’ensemble de paramètres de contexte et personnalisés qui sont passés à l’interface lorsque l’interface est appelée.

 Les informations suivantes décrivent l’interface de <xref:EnvDTE.IDTWizard> que les assistants doivent implémenter pour fonctionner dans l’IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. L’IDE appelle la méthode <xref:EnvDTE.IDTWizard.Execute%2A> sur l’Assistant, en lui transmettant les éléments suivants :

- Objet DTE

     L’objet DTE est la racine du modèle Automation.

- Handle de la boîte de dialogue de la fenêtre, comme indiqué dans le segment de code, `hwndOwner ([in] long)`.

     L’Assistant utilise cette `hwndOwner` comme parent de la boîte de dialogue de l’Assistant.

- Les paramètres de contexte passés à l’interface en tant que variante pour SAFEARRAY, comme indiqué dans le segment de code, `[in] SAFEARRAY (VARIANT)* ContextParams`.

     Les paramètres de contexte contiennent un tableau de valeurs qui sont spécifiques au type d’Assistant en cours de démarrage et à l’état actuel du projet. L’IDE transmet les paramètres de contexte à l’Assistant. Pour plus d’informations, consultez [paramètres de contexte](../../extensibility/internals/context-parameters.md).

- Paramètres personnalisés passés à l’interface en tant que variante pour SAFEARRAY, comme indiqué dans le segment de code, `[in] SAFEARRAY (VARIANT)* CustomParams`.

     Les paramètres personnalisés contiennent un tableau de paramètres définis par l’utilisateur. Un fichier. vsz passe des paramètres personnalisés à l’IDE. Les valeurs sont déterminées par les instructions `Param=`. Pour plus d’informations, consultez [paramètres personnalisés](../../extensibility/internals/custom-parameters.md).

- Les valeurs de retour de l’interface sont

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>Voir aussi
- [Paramètres de contexte](../../extensibility/internals/context-parameters.md)
- [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)
- [Assistants](../../extensibility/internals/wizards.md)
- [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)