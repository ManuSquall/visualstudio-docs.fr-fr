---
title: "CA1024&#160;: Utiliser les propri&#233;t&#233;s lorsque cela est appropri&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UsePropertiesWhereAppropriate"
  - "CA1024"
helpviewer_keywords: 
  - "CA1024"
  - "UsePropertiesWhereAppropriate"
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1024&#160;: Utiliser les propri&#233;t&#233;s lorsque cela est appropri&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UsePropertiesWhereAppropriate|  
|CheckId|CA1024|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Le nom d'une méthode publique ou protégée commence par `Get`, n'accepte aucun paramètre et retourne une valeur qui n'est pas un tableau.  
  
## Description de la règle  
 Dans la plupart des cas, les propriétés représentent des données, et les méthodes exécutent des actions.  Les propriétés sont accédées comme des champs, ce qui simplifie leur utilisation.  Une méthode est susceptible de devenir une propriété si l'une de ces conditions est présente :  
  
-   Ne prend pas d'arguments et retourne les informations d'état d'un objet.  
  
-   Accepte un argument unique pour définir quelques parties de l'état d'un objet.  
  
 Les propriétés doivent se comporter comme des champs ; si la méthode ne le peut pas, elle ne doit pas être changée en propriété.  Les méthodes sont meilleures que les propriétés dans les situations suivantes :  
  
-   La méthode exécute une opération qui prend du temps.  La méthode est perçue comme plus lente que le temps requis pour définir ou obtenir la valeur d'un champ.  
  
-   La méthode exécute une conversion.  L'accès à un champ ne retourne aucune version convertie des données qu'il stocke.  
  
-   La méthode Get présente un effet secondaire observable.  Récupérer la valeur d'un champ ne produit aucun effet secondaire.  
  
-   L'ordre d'exécution est important.  La définition de la valeur d'un champ ne s'appuie sur aucune autre opération qui s'est produite.  
  
-   L'appel à la méthode deux fois de suite génère des résultats différents.  
  
-   La méthode est statique, mais retourne un objet qui peut être modifié par l'appelant.  La récupération de la valeur d'un champ ne permet pas à l'appelant de modifier les données stockées par ce champ.  
  
-   La méthode retourne un tableau.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, changez la méthode en propriété.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle si la méthode rencontre au moins un des critères précédemment énumérés.  
  
## Contrôle de l'expansion de propriété dans le débogueur  
 L'une des raisons pour lesquelles les programmeurs évitent d'utiliser une propriété est parce qu'ils ne souhaitent pas que le débogueur la développe automatiquement.  Par exemple, la propriété pourrait impliquer d'allouer un grand objet ou d'appeler un P\/Invoke, mais elle pourrait ne pas avoir réellement d'effets secondaires observables.  
  
 Vous pouvez empêcher le débogueur de développer automatiquement les propriétés en appliquant <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>.  L'exemple suivant présente cet attribut appliqué à une propriété d'instance.  
  
```vb  
Imports System   
Imports System.Diagnostics   
  
Namespace Microsoft.Samples   
  
    Public Class TestClass   
  
        ' [...]   
  
        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _   
        Public ReadOnly Property LargeObject() As LargeObject   
            Get   
                ' Allocate large object   
                ' [...]   
            End Get   
        End Property   
  
    End Class   
  
End Namespace  
```  
  
```c#  
  
        using System;   
using System.Diagnostics;   
  
namespace Microsoft.Samples   
{   
    public class TestClass   
    {   
        // [...]   
  
        [DebuggerBrowsable(DebuggerBrowsableState.Never)]   
        public LargeObject LargeObject   
        {   
            get   
            {   
                // Allocate large object   
                // [...]   
  
        }  
    }  
}  
```  
  
## Exemple  
 L'exemple suivant contient plusieurs méthodes qui doivent être converties en propriétés, et plusieurs autres qui ne le doivent pas car elles ne se comportent pas comme champs.  
  
 [!code-cs[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]