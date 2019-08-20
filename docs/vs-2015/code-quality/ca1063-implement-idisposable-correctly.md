---
title: 'CA1063 : Implémenter IDisposable correctement | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 90f218165c0543c1881857191efd202717c6e372
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820888"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063 : Implémenter IDisposable correctement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 `IDisposable` n’est pas implémentée correctement. Parmi les raisons de ce problème sont répertoriées ici :

- IDisposable est réimplémenté dans la classe.

- Finalize est substitué à nouveau.

- Dispose est substitué.

- Dispose() n’est pas public, sealed ou nommée Dispose.

- Dispose (bool) n’est pas protégé, virtuel ou non scellé.

- Dans les types non scellés, Dispose() doit appeler Dispose (true).

- Pour les types unsealed, l’implémentation Finalize n’appelle pas un ou les deux dispose (bool) ou le finaliseur de la classe de cas.

  Violation de l’un de ces modèles déclenche cet avertissement.

  Chaque type IDisposable racine non scellé doit fournir sa propre méthode Dispose (bool) void virtuelle protégée. Dispose() doit appeler la méthode Dispose (true) et Finalize doit appeler la méthode Dispose (false). Si vous créez un type de IDisposable racine non scellé, vous devez définir dispose (bool) et l’appeler. Pour plus d’informations, consultez [de nettoyage des ressources non managées](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) dans le [instructions de conception Framework](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) section de la documentation .NET Framework.

## <a name="rule-description"></a>Description de la règle
 Tous les types IDisposable doivent implémenter le modèle Dispose correctement.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Examinez votre code et déterminer lequel des solutions suivantes corrigera cette violation.

- Supprimez IDisposable de la liste des interfaces qui est implémentée par {0} et substituez l’implémentation Dispose de la classe de base à la place.

- Supprimez le finaliseur du type {0}, substituez Dispose (bool disposing) et placez la logique de finalisation dans le chemin d’accès du code où 'disposing' a la valeur false.

- Supprimer {0}, substituez Dispose (bool disposing) et placez la logique dispose dans le chemin d’accès du code où 'disposing' a la valeur true.

- Vérifiez que {0} est déclaré comme public et sealed.

- Renommer {0} en 'Dispose' et vérifiez qu’il est déclaré comme public et sealed.

- Assurez-vous que l’option {0} est déclaré comme protected, virtual et unsealed.

- Modifiez {0} afin qu’il appelle Dispose (true), puis appelle GC. SuppressFinalize sur l’instance d’objet actuelle ('this' ou 'Me' dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), puis retourne.

- Modifiez {0} afin qu’il appelle Dispose (false) et renvoie ensuite.

- Si vous écrivez une classe racine unsealed IDisposable, assurez-vous que l’implémentation de IDisposable suit le modèle qui est décrite plus haut dans cette section.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="pseudo-code-example"></a>Exemple de pseudo-code
 Le pseudo-code suivant fournit un exemple général de la manière dont dispose (bool) doit être implémentée dans une classe qui utilise managée et les ressources natives.

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
