---
title: Interface Des assistants (IDTWizard) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1c8d728a76097321e4e1f16640cab97599d6ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703276"
---
# <a name="wizard-interface-idtwizard"></a>Interface de l’Assistant (IDTWizard)
L’environnement de développement intégré <xref:EnvDTE.IDTWizard> (IDE) utilise l’interface pour communiquer avec les sorciers. Les assistants doivent implémenter cette interface afin d’être installé dans l’IDE.

 La <xref:EnvDTE.IDTWizard.Execute%2A> méthode est la seule <xref:EnvDTE.IDTWizard> méthode associée à l’interface. Les assistants implémenter cette méthode et l’IDE appelle la méthode sur l’interface. L’exemple suivant montre la signature de la méthode.

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

 Le mécanisme de démarrage est similaire pour le **nouveau projet** et ajouter de nouveaux assistants **d’élément.** Pour commencer l’un <xref:EnvDTE.IDTWizard> ou l’autre, vous appelez l’interface définie dans Dteinternal.h. La seule différence est l’ensemble de paramètres contextuelles et personnalisés qui sont transmis à l’interface lorsque l’interface est appelée.

 Les informations suivantes <xref:EnvDTE.IDTWizard> décrivent l’interface que les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] assistants doivent mettre en œuvre pour travailler dans l’IDE. L’IDE <xref:EnvDTE.IDTWizard.Execute%2A> appelle la méthode sur le magicien, en le passant ce qui suit:

- L’objet DTE

     L’objet DTE est la racine du modèle Automation.

- La poignée de la boîte de dialogue fenêtre `hwndOwner ([in] long)`comme indiqué dans le segment de code, .

     L’assistant `hwndOwner` utilise cela comme le parent de la boîte de dialogue assistant.

- Paramètres de contexte transmis à l’interface comme variante pour `[in] SAFEARRAY (VARIANT)* ContextParams`SAFEARRAY comme indiqué dans le segment de code, .

     Les paramètres de contexte contiennent un éventail de valeurs qui sont spécifiques au type d’assistant en cours de démarrage et à l’état actuel du projet. L’IDE transmet les paramètres de contexte à l’assistant. Pour plus d’informations, voir [Paramètres contextuelles](../../extensibility/internals/context-parameters.md).

- Paramètres personnalisés transmis à l’interface comme une variante pour `[in] SAFEARRAY (VARIANT)* CustomParams`SAFEARRAY comme indiqué dans le segment de code, .

     Les paramètres personnalisés contiennent un éventail de paramètres définis par l’utilisateur. Un fichier .vsz transmet les paramètres personnalisés à l’IDE. Les valeurs sont `Param=` déterminées par les énoncés. Pour plus d’informations, voir [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md).

- Les valeurs de retour pour l’interface sont

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>Voir aussi
- [Paramètres contextuelles](../../extensibility/internals/context-parameters.md)
- [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)
- [Assistants](../../extensibility/internals/wizards.md)
- [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
