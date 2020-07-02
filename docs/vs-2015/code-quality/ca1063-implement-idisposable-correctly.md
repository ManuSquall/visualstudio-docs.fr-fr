---
title: 'CA1063 : implémenter IDisposable correctement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 04691d2344b232906676180122ad67fff5405891
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539358"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063 : Implémenter IDisposable correctement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 `IDisposable`n’est pas implémenté correctement. Les raisons de ce problème sont répertoriées ici :

- IDisposable est réimplémentée dans la classe.

- Finalize est de nouveau substitué.

- La méthode dispose est remplacée.

- Dispose () n’est pas public, sealed ni dispose nommé.

- Dispose (bool) n’est pas protégé, virtuel ou non scellé.

- Dans les types non scellés, dispose () doit appeler Dispose (true).

- Pour les types non scellés, l’implémentation Finalize n’appelle pas la méthode Dispose (bool) ou le finaliseur de classe de cas.

  Toute violation de l’un de ces modèles déclenchera cet avertissement.

  Chaque type IDisposable racine non scellé doit fournir sa propre méthode vide virtuelle void (bool). Dispose () doit appeler Dispose (true) et Finalize doit appeler Dispose (false). Si vous créez un type IDisposable racine non scellé, vous devez définir dispose (bool) et l’appeler. Pour plus d’informations, consultez [nettoyage des ressources non managées](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) dans la section [règles de conception](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) de l’infrastructure de la documentation .NET Framework.

## <a name="rule-description"></a>Description de la règle
 Tous les types IDisposable doivent implémenter le modèle Dispose correctement.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Examinez votre code et déterminez laquelle des solutions suivantes corrigera cette violation.

- Supprimez IDisposable de la liste des interfaces implémentées par {0} et remplacez l’implémentation dispose de la classe de base à la place.

- Supprimez le finaliseur du type {0} , substituez Dispose (bool disposing) et placez la logique de finalisation dans le chemin du code où’disposing’a la valeur false.

- Supprimez {0} , substituez Dispose (bool disposing) et placez la logique dispose dans le chemin du code où’disposing’a la valeur true.

- Vérifiez que {0} est déclaré comme public et sealed.

- Renommez {0} -le en’dispose’et assurez-vous qu’il est déclaré comme public et sealed.

- Assurez-vous que {0} est déclaré comme protégé, virtuel et non scellé.

- Modifiez {0} afin qu’il appelle Dispose (true), puis appelle gc. SuppressFinalize sur l’instance d’objet actuelle ('This’ou’me’dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ), puis retourne.

- Modifiez {0} afin qu’il appelle Dispose (false), puis retourne.

- Si vous écrivez une classe racine non scellée IDisposable, assurez-vous que l’implémentation de IDisposable suit le modèle décrit plus haut dans cette section.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="pseudo-code-example"></a>Exemple de pseudo-code
 Le pseudo-code suivant fournit un exemple général de la façon dont la méthode Dispose (bool) doit être implémentée dans une classe qui utilise des ressources managées et natives.

```
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

// Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }
    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources itself, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }
    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```
