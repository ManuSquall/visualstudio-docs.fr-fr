---
title: Ajout d’une propriété de suivi à une définition de Domain-Specific Language | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: 4aa47777-de75-4897-a423-a3c4426b4125
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4d53cdee5d92a92bb7405d1ecfb669e6de25a5a0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432388"
---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>Ajout d'une propriété de suivi à une définition de langage spécifique à un domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment ajouter une propriété de suivi à un modèle de domaine.  
  
 Un *suivi domaine* propriété est une propriété qui peut être mis à jour par l’utilisateur, mais qui a la valeur par défaut qui est calculée en utilisant les valeurs d’autres propriétés de domaine ou les éléments.  
  
 Par exemple, dans les outils de langage spécifique à un domaine (outils DSL), le nom d’affichage propriété d’une classe de domaine a la valeur par défaut qui est calculée en utilisant le nom de la classe de domaine, mais un utilisateur peut modifier la valeur au moment du design ou réaffectez-lui la valeur calculée.  
  
 Cette procédure pas à pas, vous allez créer un langage spécifique à un domaine (DSL) qui a une propriété qui a comme valeur par défaut basée sur la propriété Namespace de valeur par défaut du modèle de suivi de Namespace. Pour plus d’informations sur les propriétés de suivi, consultez [définissant les propriétés de suivi](http://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be).  
  
- La prise en charge d’outils DSL suivi des descripteurs de propriété. Toutefois, le concepteur DSL ne peut pas servir à ajouter une propriété de suivi à un langage. Par conséquent, vous devez ajouter un code personnalisé pour définir et implémenter la propriété de suivi.  
  
  Une propriété de suivi a deux états : suivi et de mise à jour par l’utilisateur. Propriétés de suivi présentent les caractéristiques suivantes :  
  
- En cas de l’état de suivi, la valeur de la propriété de suivi est calculée, et la valeur est mise à jour que les autres propriétés dans la modification de modèle.  
  
- Dans la mise à jour par l’état utilisateur, la valeur de la propriété de suivi conserve la valeur à laquelle l’utilisateur précédente définition de la propriété.  
  
- Dans le **propriétés** fenêtre, le **réinitialiser** commande pour la propriété de suivi est activée uniquement lorsque la propriété est dans la mise à jour par l’état utilisateur. Le **réinitialiser** commande définit la propriété de suivi à l’état de suivi.  
  
- Dans le **propriétés** fenêtre, lorsque la propriété de suivi dans le suivi de l’état, sa valeur est affichée dans une police normale.  
  
- Dans le **propriétés** fenêtre, lorsque la propriété de suivi dans la mise à jour par état de l’utilisateur, sa valeur est affichée dans une police en gras.  
  
## <a name="prerequisites"></a>Prérequis  
 Avant de commencer cette procédure pas à pas, vous devez d’abord installer ces composants :  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|[!INCLUDE[dsl](../includes/dsl-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-the-dsl-project"></a>Création du projet DSL  
 Créer le projet pour votre langage spécifique à un domaine.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
1. Créez un projet de Concepteur de langage spécifique à un domaine. Nommez-le `TrackingPropertyDSL`.  
  
2. Dans le **Assistant Concepteur de langage spécifique à un domaine**, définissez les options suivantes :  
  
    1. Sélectionnez le **MinimalLanguage** modèle.  
  
    2. Utilisez le nom par défaut pour le langage spécifique à un domaine, `TrackingPropertyDSL`.  
  
    3. Définir l’extension pour les fichiers de modèle à `trackingPropertyDsl`.  
  
    4. Utilisez l’icône de modèle par défaut pour les fichiers de modèle.  
  
    5. Définissez le nom du produit à `Product Name`.  
  
    6. Définissez le nom de la société à `Company Name`.  
  
    7. Utilisez la valeur par défaut pour l’espace de noms racine pour les projets dans la solution, `CompanyName.ProductName.TrackingPropertyDSL`.  
  
    8. Autoriser l’Assistant créer un fichier de clé de nom fort de vos assemblys.  
  
    9. Passez en revue les détails de la solution, puis cliquez sur **Terminer** pour créer le projet de définition DSL.  
  
## <a name="customizing-the-default-dsl-definition"></a>Personnalisation de la définition DSL de valeur par défaut  
 Dans cette section, vous personnalisez la définition DSL pour contenir les éléments suivants :  
  
- Un Namespace propriété pour chaque élément du modèle de suivi.  
  
- Une propriété booléenne IsNamespaceTracking pour chaque élément du modèle. Cette propriété indique si la propriété de suivi est dans l’état de suivi ou à la mise à jour par l’état utilisateur.  
  
- Une propriété Namespace par défaut pour le modèle. Cette propriété sera utilisée pour calculer la valeur par défaut de la propriété de suivi de Namespace.  
  
- Une propriété CustomElements calculé pour le modèle. Cette propriété indique la proportion des éléments qui ont un espace de noms personnalisé.  
  
#### <a name="to-add-the-domain-properties"></a>Pour ajouter les propriétés de domaine  
  
1. Dans le concepteur DSL, cliquez sur le **ExampleModel** de classe de domaine, pointez sur **ajouter**, puis cliquez sur **DomainProperty**.  
  
    1. Nommez la nouvelle propriété `DefaultNamespace`.  
  
    2. Dans le **propriétés** fenêtre pour la nouvelle propriété, définissez **la valeur par défaut** à `DefaultNamespace`et définissez **Type** à **chaîne**.  
  
2. Pour le **ExampleModel** domaine de classe, ajoutez une propriété de domaine nommée `CustomElements`.  
  
     Dans le **propriétés** fenêtre pour la nouvelle propriété, définissez **type** à **Calculated**.  
  
3. Pour le **ExampleElement** domaine de classe, ajoutez une propriété de domaine nommée `Namespace`.  
  
     Dans le **propriétés** fenêtre pour la nouvelle propriété, définissez **Is Browsable** à **False**et définissez **type** à **CustomStorage** .  
  
4. Pour le **ExampleElement** domaine de classe, ajoutez une propriété de domaine nommée `IsNamespaceTracking`.  
  
     Dans le **propriétés** fenêtre pour la nouvelle propriété, définissez **est consultable** à **False**, affectez la valeur **la valeur par défaut** à `true`et la valeur **Type** à **booléenne**.  
  
#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Pour mettre à jour les éléments de diagramme et les détails DSL  
  
1. Dans le concepteur DSL, cliquez sur le **ExampleShape** forme géométrique, pointez sur **ajouter**, puis cliquez sur **décorateur de texte**.  
  
    1. Nommez le nouvel élément décoratif de texte `NamespaceDecorator`.  
  
    2. Dans le **propriétés** fenêtre pour le décorateur de texte, définissez **Position** à **InnerBottomLeft**.  
  
2. Dans le concepteur DSL, sélectionnez la ligne qui relie le **ExampleElement** classe à la **ExampleShape** forme.  
  
    1. Dans le **détails DSL** fenêtre, sélectionnez le **mappages de décorateurs** onglet.  
  
    2. Dans le **décorateurs** liste, sélectionnez **NamespaceDecorator**, activez sa case à cocher puis, dans le **afficher la propriété** liste, sélectionnez **Namespace**.  
  
3. Dans **Explorateur DSL**, développez le **Classes de domaine** dossier, avec le bouton droit le **ExampleElement** nœud, puis cliquez sur **Ajouter nouveau domaine descripteur de Type**.  
  
    1. Développez le **ExampleElement** nœud, puis sélectionnez le **(descripteur de Type de domaine) du descripteur de Type personnalisé** nœud.  
  
    2. Dans le **propriétés** fenêtre pour le descripteur de type de domaine, définissez **personnalisé codé** à **True**.  
  
4. Dans **Explorateur DSL**, sélectionnez le **comportement de sérialisation Xml** nœud.  
  
    1. Dans le **propriétés** fenêtre, définissez **post-chargement personnalisé** à **True**.  
  
## <a name="transforming-templates"></a>Transformation de modèles  
 Maintenant que vous avez défini les classes de domaine et les propriétés pour votre DSL, vous pouvez vérifier que la définition DSL peut être transformée correctement pour régénérer le code de votre projet.  
  
#### <a name="to-transform-the-text-templates"></a>Pour transformer les modèles de texte  
  
1. Sur le **l’Explorateur de solutions** barre d’outils, cliquez sur **transformer tous les modèles**.  
  
2. Le système régénère le code pour la solution et enregistre DslDefinition.dsl. Pour plus d’informations sur le format XML des fichiers de définition, consultez [le fichier DslDefinition.dsl](../modeling/the-dsldefinition-dsl-file.md).  
  
## <a name="creating-files-for-custom-code"></a>Création de fichiers de Code personnalisé  
 Lorsque vous transformez tous les modèles, le système génère le code source qui définit votre langage spécifique à un domaine dans les projets Dsl et DslPackage. Afin que vous pouvez éviter toute interférence avec le texte généré, écrire votre code personnalisé dans les fichiers qui sont distincts à partir des fichiers de code généré.  
  
 Vous devez fournir le code de gestion de la valeur et l’état de votre propriété de suivi. Pour vous aider à distinguer votre code personnalisé à partir du code généré et afin d’éviter les conflits de nom de fichier, placez vos fichiers de code personnalisé dans un sous-dossier distinct.  
  
#### <a name="to-create-the-code-files"></a>Pour créer les fichiers de code  
  
1. Dans **l’Explorateur de solutions**, avec le bouton droit le **DSL** de projet, pointez sur **ajouter**, puis cliquez sur **nouveau dossier**. Nommez le nouveau dossier `CustomCode`.  
  
2. Cliquez sur le nouveau **CustomCode** dossier, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
3. Sélectionnez le **fichier de Code** modèle, définissez le **nom** à `NamespaceTrackingProperty.cs`, puis cliquez sur **OK**.  
  
     Le fichier NamespaceTrackingProperty.cs est créé et ouvert pour modification.  
  
4. Dans le dossier, créez les fichiers de code suivants : `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`, et `TypeDescriptor.cs`.  
  
5. Dans le **DslPackage** de projet, créez également un `CustomCode` dossier et lui ajouter un `Package.cs` fichier de code.  
  
## <a name="adding-helper-classes-to-support-tracking-properties"></a>Ajouter des Classes d’assistance pour prendre en charge des propriétés de suivi  
 Dans le fichier HelperClasses.cs, ajoutez le `TrackingHelper` et `CriticalException` classes comme suit. Vous ferez référence ces classes plus loin dans cette procédure pas à pas.  
  
#### <a name="to-add-the-helper-classes"></a>Pour ajouter les classes d’assistance  
  
1. Ajoutez le code suivant au fichier HelperClasses.cs.  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        internal static class TrackingHelper  
        {  
            /// <summary>Notify each model element in a collection that a tracked  
            /// property has changed.</summary>  
            /// <param name="store">The store for the model.</param>  
            /// <param name="collection">The collection of model elements that  
            /// contain the tracking property.</param>  
            /// <param name="propertyId">The ID of the tracking property.</param>  
            /// <param name="trackingPropertyId">The ID of the property that  
            /// indicates whether the tracking property is tracking.</param>  
            internal static void UpdateTrackingCollectionProperty(  
                Store store,  
                IEnumerable collection,  
                Guid propertyId,  
                Guid trackingPropertyId)  
            {  
                DomainPropertyInfo propInfo =  
                    store.DomainDataDirectory.GetDomainProperty(propertyId);  
  
                DomainPropertyInfo trackingPropInfo =  
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);  
  
                Debug.Assert(propInfo != null);  
                Debug.Assert(trackingPropInfo != null);  
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),  
                    "Tracking property not specified as a boolean");  
  
                foreach (ModelElement element in collection)  
                {  
                    // If the tracking property is currently tracking, then notify  
                    // it that the tracked property has changed.  
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);  
                    if (isTracking)  
                    {  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
            }  
        }  
  
        /// <summary>Helper class to flag critical exceptions from ones that are  
        /// safe to ignore.</summary>  
        internal static class CriticalException  
        {  
            /// <summary>Gets whether an exception is critical and can not be  
            /// ignored.</summary>  
            /// <param name="ex">The exception to check.</param>  
            /// <returns>True if the exception is critical.</returns>  
            internal static bool IsCriticalException(Exception ex)  
            {  
                if (ex is NullReferenceException  
                    || ex is StackOverflowException  
                    || ex is OutOfMemoryException  
                    || ex is System.Threading.ThreadAbortException)  
                    return true;  
  
                if (ex.InnerException != null)  
                    return IsCriticalException(ex.InnerException);  
  
                return false;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-custom-type-descriptor"></a>Ajouter du Code personnalisé pour le descripteur de Type personnalisé  
 Implémentez le `GetCustomProperties` méthode pour le descripteur de type pour le `ExampleModel` de classe de domaine.  
  
> [!NOTE]
> Le code généré par les outils DSL pour le descripteur de type personnalisé pour `ExampleModel` appels `GetCustomProperties`; Toutefois, les outils DSL ne génèrent pas de code qui implémente la méthode.  
  
 Définition de cette méthode crée le suivi descripteur de propriété pour la propriété de suivi de Namespace. En outre, en fournissant des attributs pour la propriété de suivi permet le **propriétés** fenêtre pour afficher la propriété correctement.  
  
#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Pour modifier le descripteur de type pour la classe de domaine ExampleModel  
  
1. Ajoutez le code suivant au fichier TypeDescriptor.cs.  
  
    ```csharp  
    using System;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the custom type descriptor for the ExampleElement domain class, add  
        // the GetCustomProperties method.  
        public partial class ExampleElementTypeDescriptor  
        {  
            /// <summary>Returns the property descriptors for the described  
            /// ExampleElement domain class.</summary>  
            /// <remarks>This method adds the tracking property descriptor.  
            /// </remarks>  
            private PropertyDescriptorCollection GetCustomProperties(  
                Attribute[] attributes)  
            {  
                // Get the default property descriptors from the base class  
                PropertyDescriptorCollection propertyDescriptors =  
                    base.GetProperties(attributes);  
  
                // Get a reference to the model element that is being described.  
                ExampleElement source = this.ModelElement as ExampleElement;  
  
                //Add the descriptor for the tracking property.  
                if (source != null)  
                {  
                    DomainPropertyInfo domainProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.NamespaceDomainPropertyId);  
  
                    DomainPropertyInfo trackingProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);  
  
                    // Define attributes for the tracking property so that the  
                    // Properties window displays the property correctly.  
                    Attribute[] attr = new Attribute[] {  
                        new DisplayNameAttribute("Element Namespace"),  
                        new DescriptionAttribute("The namespace of the element."),  
                        new CategoryAttribute("Tracking Properties"),  
                    };  
  
                    propertyDescriptors.Add(new TrackingPropertyDescriptor(  
                        source, domainProperty, trackingProperty, attr));  
                }  
  
                // Return the property descriptors for this element  
                return propertyDescriptors;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-package"></a>Ajouter du Code personnalisé pour le Package  
 Le code généré définit un fournisseur de description de type pour la classe de domaine ExampleElement ; Toutefois, vous devez ajouter le code pour indiquer à la solution DSL d’utiliser ce fournisseur de description de type.  
  
#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>Pour mettre à jour le package DSL pour utiliser le descripteur de type personnalisé  
  
1. Ajoutez le code suivant dans le fichier Package.cs.  
  
    ```csharp  
    using System.ComponentModel;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // Override the default Initialize method.  
        internal sealed partial class TrackingPropertyDSLPackage  
        {  
            protected override void Initialize()  
            {  
                // Add the custom type descriptor for the ExampleElement type.  
                TypeDescriptor.AddProvider(  
                    new ExampleElementTypeDescriptionProvider(),  
                    typeof(ExampleElement));  
  
                base.Initialize();  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-model"></a>Ajouter du Code personnalisé pour le modèle  
 Implémentez le `GetCustomElementsValue` méthode pour le `ExampleModel` de classe de domaine.  
  
> [!NOTE]
> Le code généré par les outils DSL pour `ExampleModel` appels `GetCustomElementsValue`; Toutefois, les outils DSL ne génèrent pas de code qui implémente la méthode.  
  
 Définition de la `GetCustomElementsValue` méthode fournit la logique pour la propriété CustomElements calculé de `ExampleModel`. Cette méthode compte le nombre de `ExampleElement` des classes de domaine qui ont une propriété qui a une valeur utilisateur mis à jour et retourne une chaîne qui représente ce nombre sous forme de proportion du total des éléments dans le modèle de suivi de Namespace.  
  
 En outre, ajoutez un `OnDefaultNamespaceChanged` méthode à `ExampleModel`et remplacer le `OnValueChanged` méthode de la `DefaultNamespacePropertyHandler` imbriqués de classe de `ExampleModel` pour appeler `OnDefaultNamespaceChanged`.  
  
 Étant donné que la propriété DefaultNamespace est utilisée pour calculer la propriété, de suivi de Namespace `ExampleModel` doit notifier tous les `ExampleElement` des classes de domaine que la valeur de DefaultNamespace a changé.  
  
#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Pour modifier le Gestionnaire de propriétés pour la propriété suivie  
  
1. Ajoutez le code suivant au fichier ExampleModel.cs.  
  
    ```csharp  
    using System.Linq;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        public partial class ExampleModel  
        {  
            public string GetCustomElementsValue()  
            {  
                if (this.Elements.Count == 0) return "0/0";  
  
                int number = this.Elements.Count(e => !e.IsNamespaceTracking);  
                return string.Format("{0}/{1}", number, this.Elements.Count);  
            }  
  
            #region Value changed handler for the tracked property  
  
            // When a tracked property changes, it needs to notify all of the properties  
            // that track it.  
  
            /// <summary>Called by the DefaultNamespace property value handler when the  
            /// DefaultNamespace property changes.</summary>  
            /// <param name="oldValue">The previous value of the property.</param>  
            /// <param name="newValue">The new value of the property.</param>  
            protected virtual void OnDefaultNamespaceChanged(  
                string oldValue, string newValue)  
            {  
                // Use the helper class to notify all of the elements in the model  
                // that the default namespace has changed.  
                TrackingHelper.UpdateTrackingCollectionProperty(  
                    this.Store,  
                    this.Elements,  
                    ExampleElement.NamespaceDomainPropertyId,  
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);  
            }  
  
            // Update the change handler for the DefaultNamespace property.  
            internal sealed partial class DefaultNamespacePropertyHandler  
            {  
                /// <summary>Called when the DefaultNamespace property changes.</summary>  
                /// <param name="element">The model element that has the property that  
                /// changed.</param>  
                /// <param name="oldValue">The previous value of the property.</param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleModel element, string oldValue, string newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
  
                    if (!element.Store.InUndoRedoOrRollback)  
                    {  
                        element.OnDefaultNamespaceChanged(oldValue, newValue);  
                    }  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-tracking-property"></a>Ajouter du Code personnalisé pour la propriété de suivi  
 Ajouter un `CalculateNamespace` méthode à la `ExampleElement` de classe de domaine.  
  
 Définition de cette méthode fournit la logique pour la propriété CustomElements calculé de `ExampleModel`. Cette méthode compte le nombre de `ExampleElement` des classes de domaine qui ont une propriété qui se trouve dans la mise à jour de suivi de Namespace par état de l’utilisateur et retourne une chaîne qui représente ce nombre sous forme de proportion du total des éléments dans le modèle.  
  
 En outre, ajouter pour le stockage et des méthodes pour obtenir et définir, la propriété de stockage personnalisé Namespace de le `ExampleElement` de classe de domaine.  
  
> [!NOTE]
> Le code généré par les outils DSL pour `ExampleModel` appelle la méthode get et définir des méthodes ; Toutefois, les outils DSL ne génèrent pas de code qui implémente les méthodes.  
  
#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Pour ajouter la méthode pour le descripteur de type personnalisé  
  
1. Ajoutez le code suivant au fichier NamespaceTrackingProperty.cs.  
  
    ```csharp  
    using System;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the domain class that has the tracking property, add the caluclation  
        // for when the property is tracking.  
        public partial class ExampleElement  
        {  
            /// <summary>Calculates the actual value of the property when it is  
            /// tracking.</summary>  
            /// <returns>The value of the tracking property when it is  
            /// tracking.</returns>  
            /// <remarks>Making this method virtual allows child classes to modify  
            /// the calculation. This method does not need to perform validation, as  
            /// its caller handles validation prior to calling this method.  
            /// <para>In this case, the tracking value depends on the default namespace  
            /// property of the parent model.</para></remarks>  
            protected virtual string CalculateNamespace()  
            {  
                return this.ExampleModel.DefaultNamespace;  
            }  
  
            #region Tracking property implementation  
  
            // Implement the Namespace domain property of the ExampleElement domain class,  
            // and update the IsNamespaceTracking domain property value handler.  
  
            /// <summary>Storage for the Namespace property.</summary>  
            private string namespaceStorage;  
  
            /// <summary>Gets the value of the Namespace property.</summary>  
            /// <returns>The value of the Namespace property.</returns>  
            private string GetNamespaceValue()  
            {  
                // Only retrieve the tracked value if the store is not in the  
                // middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!loading && this.IsNamespaceTracking)  
                {  
                    try  
                    {  
                        return this.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                        return default(string);  
                    }  
                    catch (Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                        else  
                        {  
                            return default(string);  
                        }  
                    }  
                }  
  
                return namespaceStorage;  
            }  
  
            /// <summary>Sets the value of the Namespace property.</summary>  
            /// <param name="value">The new value for the property.</param>  
            private void SetNamespaceValue(string value)  
            {  
                namespaceStorage = value;  
  
                // Only update the state of the tracking property if the store is  
                // not in the middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!this.Store.InUndoRedoOrRollback && !loading)  
                {  
                    this.IsNamespaceTracking = false;  
                }  
            }  
  
            // Update the default behavior of the ExampleElement.IsNamespaceTracking  
            // domain property value handler.  
            internal sealed partial class IsNamespaceTrackingPropertyHandler  
            {  
                /// <summary>Called after the IsNamespaceTracking property changes.  
                /// </summary>  
                /// <param name="element">The model element that has the property  
                /// that changed.</param>  
                /// <param name="oldValue">The previous value of the property.  
                /// </param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleElement element, Boolean oldValue, Boolean newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
                    if (!element.Store.InUndoRedoOrRollback && newValue)  
                    {  
                        DomainPropertyInfo propInfo =  
                            element.Store.DomainDataDirectory.GetDomainProperty(  
                                ExampleElement.NamespaceDomainPropertyId);  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
  
                /// <summary>Performs the reset operation for the IsNamespaceTracking  
                /// property for a model element.</summary>  
                /// <param name="element">The model element that has the property  
                /// to reset.</param>  
                internal void ResetValue(ExampleElement element)  
                {  
                    object calculatedValue = null;  
  
                    try  
                    {  
                        calculatedValue = element.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                    }  
                    catch (System.Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                    }  
  
                    if ((calculatedValue != null  
                        && object.Equals(element.Namespace, calculatedValue)))  
                    {  
                        element.isNamespaceTrackingPropertyStorage = true;  
                    }  
                }  
  
                /// <summary>Method to set IsNamespaceTracking to false so that this  
                /// instance of this tracking property is not storage-based.  
                /// </summary>  
                /// <param name="element">The element on which to reset the property  
                /// value.</param>  
                internal void PreResetValue(ExampleElement element)  
                {  
                    // Force the IsNamespaceTracking property to false so that the value  
                    // of the Namespace property is retrieved from storage.  
                    element.isNamespaceTrackingPropertyStorage = false;  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-to-support-serialization"></a>Ajouter du Code personnalisé pour prendre en charge la sérialisation  
 Ajoutez le code pour prendre en charge le comportement de post-chargement personnalisé pour la sérialisation XML.  
  
> [!NOTE]
> Le code que les outils DSL générer des appels le `OnPostLoadModel` et `OnPostLoadModelAndDiagram` méthodes ; Toutefois, les outils DSL ne génèrent pas de code qui implémente ces méthodes.  
  
#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Pour ajouter du code pour prendre en charge le comportement de post-chargement personnalisé  
  
1. Ajoutez le code suivant au fichier Serialization.cs.  
  
    ```csharp  
    using System;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        #region Helper classes for maintaining state while the store is serializing.  
  
        public abstract partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Reset the tracking state properties to their natural values  
            /// based on comparing storage with calculation.</summary>  
            /// <param name="store">The store that contains this model.</param>  
            internal static void ResetTrackingProperties(Store store)  
            {  
                // Two passes required - one to set all elements to storage-based  
                // then another to set some back to being tracking.  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.PreResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.ResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
            }  
        }  
  
        // Add the pre-reset and reset methods for the model element.  
        public partial class ExampleElement  
        {  
            /// <summary>Calls the pre-reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void PreResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);  
            }  
  
            /// <summary>Calls the reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void ResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);  
            }  
        }  
  
        #endregion  
  
        #region Custom serialization code  
  
        // To the serialization helper for the TrackingPropertyDSL class, add post  
        // load handlers to bind the tracking property to the serialization process.  
        // These handlers manage the tracking states and property values when the  
        // model is serialized and deserialized.  
        public partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Customize model loading.</summary>  
            /// <param name="serializationResult">The serialization result from the  
            /// load operation.</param>  
            /// <param name="partition">The partition in which the new  
            /// instance was created.</param>  
            /// <param name="fileName">The name of the file from which the  
            /// instance was deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.  
            /// </param>  
            private void OnPostLoadModel(  
                SerializationResult serializationResult,  
                Partition partition,  
                string fileName,  
                ExampleModel modelRoot)  
            {  
            }  
  
            /// <summary>Customize model and diagram loading.</summary>  
            /// <param name="serializationResult">Stores serialization result from  
            /// the load operation.</param>  
            /// <param name="modelPartition">Partition in which the new  
            /// instance will be created.</param>  
            /// <param name="modelFileName">Name of the file from which the  
            /// instance will be deserialized.</param>  
            /// <param name="diagramPartition">Partition in which the new  
            /// diagram instance will be created.</param>  
            /// <param name="diagramFileName">Name of the file from which the  
            /// diagram instance will be deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.</param>  
            /// <param name="diagram">The diagram matching the modelRoot.</param>  
            private void OnPostLoadModelAndDiagram(  
                SerializationResult serializationResult,  
                Partition modelPartition,  
                string modelFileName,  
                Partition diagramPartition,  
                string diagramFileName,  
                ExampleModel modelRoot,  
                TrackingPropertyDSLDiagram diagram)  
            {  
                Debug.Assert(modelPartition != null);  
                Debug.Assert(modelPartition.Store != null);  
  
                // Tracking properties need to be set up according to whether the  
                // serialization matches the calculated values.  
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(  
                    modelPartition.Store);  
            }  
        }  
  
        #endregion  
    }  
    ```  
  
## <a name="testing-the-language"></a>Test de la langue  
 L’étape suivante consiste à générer et exécuter le concepteur DSL dans une nouvelle instance de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] afin que vous puissiez vérifier que la propriété de suivi fonctionne correctement.  
  
#### <a name="to-exercise-the-language"></a>Pour tester la langue  
  
1. Dans le menu **Générer**, cliquez sur **Régénérer la solution**.  
  
2. Dans le menu **Déboguer**, cliquez sur **Démarrer le débogage**.  
  
     La build expérimentale de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] ouvre le **débogage** solution, qui contient un fichier de test vide.  
  
3. Dans **l’Explorateur de solutions**, double-cliquez sur le fichier Test.trackingPropertyDsl pour l’ouvrir dans le concepteur, puis cliquez sur l’aire de conception.  
  
     Notez que dans le **propriétés** fenêtre pour le diagramme, le **Namespace par défaut** propriété est **DefaultNamespace**et le **personnalisé éléments** est propriété **0/0**.  
  
4. Faites glisser un **ExampleElement** élément à partir de la **boîte à outils** à la surface du diagramme.  
  
5. Dans le **propriétés** fenêtre pour l’élément, sélectionnez le **élément Namespace** propriété et remplacez la valeur **DefaultNamespace** à  **OtherNamespace**.  
  
     Notez que la valeur de **élément Namespace** est maintenant affichée en gras.  
  
6. Dans le **propriétés** fenêtre, avec le bouton droit **élément Namespace**, puis cliquez sur **réinitialiser**.  
  
     La valeur de la propriété est modifiée pour **DefaultNamespace**, et la valeur est affichée dans une police normale.  
  
     Avec le bouton droit **élément Namespace** à nouveau. Le **réinitialiser** commande est désormais désactivée, car la propriété est actuellement dans son état de suivi.  
  
7. Faites glisser un autre **ExampleElement** à partir de la **boîte à outils** à la surface du diagramme, puis remplacez son **élément Namespace** à **OtherNamespace**.  
  
8. Cliquez sur l’aire de conception.  
  
     Dans le **propriétés** fenêtre pour le diagramme, la valeur de **personnalisé éléments** est désormais **1/2**.  
  
9. Modification **Namespace par défaut** pour le diagramme à partir de **DefaultNamespace** à **NewNamespace**.  
  
     Le **Namespace** des pistes du premier élément du **Namespace par défaut** propriété, tandis que le **Namespace** du deuxième élément conserve sa valeur utilisateur mis à jour de  **OtherNamespace**.  
  
10. Enregistrer la solution, puis fermez la build expérimentale.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Si vous envisagez d’utiliser la propriété de suivi de plusieurs ou implémenter des propriétés de suivi dans plusieurs DSL, vous pouvez créer un modèle de texte pour générer le code commun pour la prise en charge de chaque propriété de suivi. Pour plus d’informations sur les modèles de texte, consultez [génération de Code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>   
 <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>   
 [Comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)   
 [Guide pratique pour Créer une Solution de langage spécifique à un domaine](../modeling/how-to-create-a-domain-specific-language-solution.md)   
 [Procédure pas à pas : Personnalisation de la définition de Domain-Specific Language](../misc/walkthrough-customizing-the-domain-specific-language-definition.md)
