---
title: "CA1063&#160;: Impl&#233;menter IDisposable correctement | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ImplementIDisposableCorrectly"
  - "CA1063"
helpviewer_keywords: 
  - "CA1063"
  - "ImplementIDisposableCorrectly"
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1063&#160;: Impl&#233;menter IDisposable correctement
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementIDisposableCorrectly|  
|CheckId|CA1063|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 `IDisposable` n'est pas correctement implémentée.  Voici quelques\-unes des raisons de ce problème :  
  
-   IDisposable est réimplémenté dans la classe.  
  
-   Finalize est substitué à nouveau.  
  
-   Dispose est substitué.  
  
-   Dispose\(\) n'est pas public, scellé ni Dispose nommé.  
  
-   Dispose\(bool\) n'est pas protégé, virtuel ou non scellé.  
  
-   Dans les types non scellés, Dispose\(\) doit appeler Dispose\(true\).  
  
-   Pour les types non scellés, l'implémentation Finalize n'appelle pas Dispose\(bool\), ni le finaliseur de classe case, ni les deux.  
  
 La violation de l'un de ces cas déclenche cet avertissement.  
  
 Chaque type IDisposable racine non scellé doit fournir sa propre méthode Dispose\(bool\) void virtuelle protégée.  Dispose\(\) doit appeler Dipose\(true\) et Finalize doit appeler Dispose\(false\).  Si vous créez un type IDisposable racine non scellé, vous devez définir Dispose\(bool\) et l'appeler.  Pour plus d'informations, consultez [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md) dans la section [Instructions de conception d’infrastructure](../Topic/Framework%20Design%20Guidelines.md) de la documentation du .NET Framework.  
  
## Description de la règle  
 Tous les types IDisposable doivent implémenter le modèle Dispose correctement.  
  
## Comment corriger les violations  
 Examinez votre code et déterminez laquelle des solutions suivantes corrigera cette violation.  
  
-   Supprimez IDisposable de la liste des interfaces implémentées par {0} et substituez l'implémentation Dispose de la classe de base.  
  
-   Supprimez le finaliseur du type {0}, substituez Dispose\(bool disposing\) et placez la logique de finalisation dans le chemin du code où 'disposing' a la valeur False.  
  
-   Supprimez {0}, substituez Dispose\(bool disposing\) et placez la logique dispose dans le chemin du code où 'disposing' a la valeur True.  
  
-   Assurez\-vous que {0} est déclaré comme public et sealed.  
  
-   Renommez {0} en 'Dispose' et vérifiez qu'il est déclaré comme public et sealed.  
  
-   Vérifiez que {0} est déclaré comme protected, virtual et unsealed.  
  
-   Modifiez {0} afin qu'il appelle Dispose\(true\) et GC.SuppressFinalize sur l'instance de l'objet en cours \('this' ou 'Me' en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) puis qu'il retourne une valeur.  
  
-   Modifiez {0} afin qu'il appelle Dispose\(false\) et qu'il retourne une valeur.  
  
-   Si vous écrivez une classe racine unsealed IDisposable, assurez\-vous que l'implémentation IDisposable suit le modèle décrit plus tôt dans cette section.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple de pseudo\-code  
 Le pseudo\-code suivant fournit un exemple général de la manière dont Dispose\(bool\) doit être implémenté dans une classe qui utilise les ressources managées et natives.  
  
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