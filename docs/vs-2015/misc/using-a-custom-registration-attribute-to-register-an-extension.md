---
title: À l’aide d’un attribut personnalisé d’inscription pour inscrire une Extension | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: jillfra
ms.openlocfilehash: a619c5d418df3b9b85ab09cf9b907617ebd81b67
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935782"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>Utilisation d’un attribut d’inscription personnalisé pour inscrire une extension
Dans certains cas, vous devrez peut-être créer un nouvel attribut d’inscription pour votre extension. Vous pouvez utiliser les attributs d’inscription pour ajouter de nouvelles clés de Registre ou pour ajouter de nouvelles valeurs pour les clés existantes. Le nouvel attribut doit dériver de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, et il doit remplacer le <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> et <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> méthodes.  
  
## <a name="creating-a-custom-attribute"></a>Création d’un attribut personnalisé  
 Le code suivant montre comment créer un nouvel attribut d’inscription.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 Le <xref:System.AttributeUsageAttribute> est utilisé sur les classes d’attributs pour spécifier l’élément de programme (classe, méthode, etc.) à laquelle l’attribut se rapporte, qu’il peut être utilisé plusieurs fois et si elle peut être héritée.  
  
### <a name="creating-a-registry-key"></a>Création d’une clé de Registre  
 Dans le code suivant, l’attribut personnalisé crée un **personnalisé** sous-clé sous la clé pour le VSPackage est en cours d’inscription.  
  
```  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Création d’une nouvelle valeur sous une clé de Registre existante  
 Vous pouvez ajouter des valeurs personnalisées à une clé existante. Le code suivant montre comment ajouter une nouvelle valeur à une clé d’inscription de VSPackage.  
  
```  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
  
```