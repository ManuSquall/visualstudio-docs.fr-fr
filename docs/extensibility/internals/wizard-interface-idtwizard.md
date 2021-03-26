---
title: Interface de l’Assistant (IDTWizard) | Microsoft Docs
description: L’IDE utilise l’interface IDTWizard pour communiquer avec les assistants. Les assistants doivent implémenter cette interface pour être installés dans l’IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b8dc88341bc72755ae0f5011d18182c5b78bb483
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074195"
---
# <a name="wizard-interface-idtwizard"></a>Interface de l’Assistant (IDTWizard)
L’environnement de développement intégré (IDE) utilise l' <xref:EnvDTE.IDTWizard> interface pour communiquer avec les assistants. Les assistants doivent implémenter cette interface pour être installés dans l’IDE.

 La <xref:EnvDTE.IDTWizard.Execute%2A> méthode est la seule méthode associée à l' <xref:EnvDTE.IDTWizard> interface. Les assistants implémentent cette méthode et l’IDE appelle la méthode sur l’interface. L’exemple suivant illustre la signature de la méthode.

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

 Le mécanisme de démarrage est similaire pour les assistants **nouveau projet** et **Ajouter un nouvel élément** . Pour démarrer l’un ou l’autre, vous devez appeler l' <xref:EnvDTE.IDTWizard> interface définie dans Dteinternal. h. La seule différence est l’ensemble de paramètres de contexte et personnalisés qui sont passés à l’interface lorsque l’interface est appelée.

 Les informations suivantes décrivent l' <xref:EnvDTE.IDTWizard> interface que les assistants doivent implémenter pour fonctionner dans l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. L’IDE appelle la <xref:EnvDTE.IDTWizard.Execute%2A> méthode sur l’Assistant, en lui transmettant les éléments suivants :

- Objet DTE

     L’objet DTE est la racine du modèle Automation.

- Handle de la boîte de dialogue de la fenêtre, comme indiqué dans le segment de code, `hwndOwner ([in] long)` .

     L’Assistant utilise ce `hwndOwner` en tant que parent de la boîte de dialogue de l’Assistant.

- Paramètres de contexte passés à l’interface en tant que variante pour SAFEARRAY, comme indiqué dans le segment de code, `[in] SAFEARRAY (VARIANT)* ContextParams` .

     Les paramètres de contexte contiennent un tableau de valeurs qui sont spécifiques au type d’Assistant en cours de démarrage et à l’état actuel du projet. L’IDE transmet les paramètres de contexte à l’Assistant. Pour plus d’informations, consultez [paramètres de contexte](../../extensibility/internals/context-parameters.md).

- Paramètres personnalisés passés à l’interface en tant que variante pour SAFEARRAY, comme indiqué dans le segment de code, `[in] SAFEARRAY (VARIANT)* CustomParams` .

     Les paramètres personnalisés contiennent un tableau de paramètres définis par l’utilisateur. Un fichier. vsz passe des paramètres personnalisés à l’IDE. Les valeurs sont déterminées par les `Param=` instructions. Pour plus d’informations, consultez [paramètres personnalisés](../../extensibility/internals/custom-parameters.md).

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
