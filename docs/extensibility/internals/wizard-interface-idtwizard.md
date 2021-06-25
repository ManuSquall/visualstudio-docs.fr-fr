---
title: Interface de l’Assistant (IDTWizard) | Microsoft Docs
description: L’IDE utilise l’interface IDTWizard pour communiquer avec les assistants. Les assistants doivent implémenter cette interface pour être installés dans l’IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 930996de7fa5366463ec2d60f7cf96d941f6c243
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898615"
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
