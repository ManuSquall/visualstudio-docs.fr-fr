---
title: 'CA1063 : Implémenter IDisposable correctement'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: f1b2c5b447d796ddd2098a6500b6094478fcd8b9
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842007"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063 : Implémenter IDisposable correctement

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Le <xref:System.IDisposable?displayProperty=nameWithType> interface n’est pas implémentée correctement. Raisons possibles sont les suivantes :

- <xref:System.IDisposable> est réimplémentée dans la classe.

- Finaliser est reoverridden.

- Dispose() est remplacée.

- La méthode Dispose() n’est pas publique, [sealed](/dotnet/csharp/language-reference/keywords/sealed), ou nommé **Dispose**.

- Dispose (bool) n’est pas protégé, virtuel ou non scellé.

- Dans les types non scellés, Dispose() doit appeler Dispose (true).

- Pour les types unsealed, l’implémentation Finalize n’appelle pas un ou les deux dispose (bool) ou le finaliseur de la classe de base.

Violation de l’un de ces modèles déclenche l’avertissement CA1063.

Chaque type unsealed qui déclare et implémente la <xref:System.IDisposable> interface doit fournir son propre `protected virtual void Dispose(bool)` (méthode). `Dispose()` doit appeler `Dipose(true)`, et le finaliseur doit appeler `Dispose(false)`. Si vous créez un type unsealed qui déclare et implémente la <xref:System.IDisposable> interface, vous devez définir `Dispose(bool)` et appelez-le. Pour plus d’informations, consultez [nettoyer les ressources non managées (guide .NET)](/dotnet/standard/garbage-collection/unmanaged) et [modèle Dispose](/dotnet/standard/design-guidelines/dispose-pattern).

Par défaut, cette règle examine uniquement les types visibles de l’extérieur, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Tous les <xref:System.IDisposable> types doivent implémenter le [modèle Dispose](/dotnet/standard/design-guidelines/dispose-pattern) correctement.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Examinez votre code et déterminer lequel des solutions suivantes corrigera cette violation :

- Supprimer <xref:System.IDisposable> dans la liste des interfaces qui sont implémentées par votre type et substituez l’implémentation de Dispose de la classe de base à la place.

- Supprimer le finaliseur de votre type, substituez Dispose (bool disposing) et placez la logique de finalisation dans le chemin d’accès du code où 'disposing' a la valeur false.

- Substituez Dispose (bool disposing) et placez la logique dispose dans le chemin d’accès du code où 'disposing' a la valeur true.

- Assurez-vous que Dispose() est déclaré comme public et [sealed](/dotnet/csharp/language-reference/keywords/sealed).

- Renommer votre méthode dispose pour **Dispose** et assurez-vous qu’il est déclaré comme public et [sealed](/dotnet/csharp/language-reference/keywords/sealed).

- Vérifiez que dispose (bool) est déclaré comme protected, virtuel et non scellé.

- Modifier Dispose() afin qu’il appelle Dispose (true), puis appelle <xref:System.GC.SuppressFinalize%2A> sur l’instance d’objet actuelle (`this`, ou `Me` en Visual Basic), puis retourne.

- Modifiez votre finaliseur afin qu’il appelle Dispose (false), puis retourne.

- Si vous créez un type unsealed qui déclare et implémente la <xref:System.IDisposable> l’interface, assurez-vous que l’implémentation de <xref:System.IDisposable> suit le modèle qui est décrite plus haut dans cette section.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1063.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="pseudo-code-example"></a>Exemple de pseudo-code

Le pseudo-code suivant fournit un exemple général de la manière dont dispose (bool) doit être implémentée dans une classe qui utilise managée et les ressources natives.

```csharp
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
    // own unmanaged resources, but leave the other methods
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

## <a name="see-also"></a>Voir aussi

- [Dispose, modèle (instructions de conception de framework)](/dotnet/standard/design-guidelines/dispose-pattern)
- [Nettoyer les ressources non managées (guide .NET)](/dotnet/standard/garbage-collection/unmanaged)