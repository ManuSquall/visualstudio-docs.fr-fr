---
title: Ajouter une propriété de suivi à une définition DSL
description: En savoir plus sur la propriété de domaine de suivi et sur la façon dont vous pouvez ajouter une propriété de suivi à un modèle de domaine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 546636ec3de4656bf0f6480dfaa5141d38e963d6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384913"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>Ajouter une propriété de suivi à une définition de langage spécifique à un domaine

Cette procédure pas à pas montre comment ajouter une propriété de suivi à un modèle de domaine.

Une propriété de *domaine de suivi* est une propriété qui peut être mise à jour par l’utilisateur mais dont la valeur par défaut est calculée à l’aide des valeurs d’autres propriétés ou éléments du domaine.

Par exemple, dans les outils de langage Domain-Specific (outils DSL), la propriété nom complet d’une classe de domaine a une valeur par défaut calculée à l’aide du nom de la classe de domaine, mais un utilisateur peut modifier la valeur au moment de la conception ou la réinitialiser à la valeur calculée.

Dans cette procédure pas à pas, vous créez un langage spécifique à un domaine (DSL) qui a une propriété de suivi d’espace de noms qui a une valeur par défaut basée sur la propriété d’espace de noms par défaut du modèle. Pour plus d’informations sur les propriétés de suivi, consultez [définition des propriétés de suivi](/previous-versions/cc825929(v=vs.100)).

- Les outils DSL prennent en charge les descripteurs de propriété de suivi. Toutefois, le concepteur DSL ne peut pas être utilisé pour ajouter une propriété de suivi à une langue. Par conséquent, vous devez ajouter du code personnalisé pour définir et implémenter la propriété de suivi.

  Une propriété de suivi a deux États : suivi et mis à jour par l’utilisateur. Les propriétés de suivi ont les fonctionnalités suivantes :

- Dans l’état de suivi, la valeur de la propriété Tracking est calculée et la valeur est mise à jour à mesure que d’autres propriétés du modèle changent.

- Dans l’État mis à jour par l’utilisateur, la valeur de la propriété Tracking conserve la valeur dans laquelle l’utilisateur a défini la propriété pour la dernière fois.

- Dans la fenêtre **Propriétés** , la commande de **réinitialisation** de la propriété de suivi est activée uniquement lorsque la propriété est dans l’État mis à jour par l’utilisateur. La commande de **réinitialisation** définit l’état de la propriété de suivi sur Tracking.

- Dans la fenêtre **Propriétés** , lorsque la propriété de suivi est dans l’état de suivi, sa valeur est affichée dans une police normale.

- Dans la fenêtre **Propriétés** , lorsque la propriété Tracking est dans l’État mis à jour par l’utilisateur, sa valeur est affichée en gras.

## <a name="prerequisites"></a>Prérequis

Avant de commencer cette procédure pas à pas, vous devez d’abord installer les composants suivants :

| Composant | Lien |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkID=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true) |
| [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185581](https://code.msdn.microsoft.com/site/search?query=%22Modeling%20SDK%22&f%5B0%5D.Value=%22Modeling%20SDK%22&f%5B0%5D.Type=SearchText&ac=5) |

## <a name="create-the-project"></a>Créer le projet

1. Créez un projet Domain-Specific Language designer. Nommez-le `TrackingPropertyDSL`.

2. Dans l' **assistant concepteur Domain-specific language**, définissez les options suivantes :

    1. Sélectionnez le modèle **MinimalLanguage** .

    2. Utilisez le nom par défaut pour le langage spécifique à un domaine, `TrackingPropertyDSL` .

    3. Définissez l’extension des fichiers de modèle sur `trackingPropertyDsl` .

    4. Utilisez l’icône de modèle par défaut pour les fichiers de modèle.

    5. Définissez le nom du produit sur `Product Name` .

    6. Définissez le nom de la société sur `Company Name` .

    7. Utilisez la valeur par défaut pour l’espace de noms racine des projets dans la solution, `CompanyName.ProductName.TrackingPropertyDSL` .

    8. Autorisez l’Assistant à créer un fichier de clé de nom fort pour vos assemblys.

    9. Passez en revue les détails de la solution, puis cliquez sur **Terminer** pour créer le projet de définition DSL.

## <a name="customize-the-default-dsl-definition"></a>Personnaliser la définition DSL par défaut
 Dans cette section, vous allez personnaliser la définition DSL pour qu’elle contienne les éléments suivants :

- Propriété de suivi d’espace de noms pour chaque élément du modèle.

- Propriété booléenne IsNamespaceTracking pour chaque élément du modèle. Cette propriété indique si la propriété de suivi est dans l’état de suivi ou dans l’État mis à jour par l’utilisateur.

- Propriété d’espace de noms par défaut pour le modèle. Cette propriété sera utilisée pour calculer la valeur par défaut de la propriété de suivi d’espace de noms.

- Propriété calculée CustomElements pour le modèle. Cette propriété indique la proportion d’éléments qui ont un espace de noms personnalisé.

### <a name="to-add-the-domain-properties"></a>Pour ajouter les propriétés de domaine

1. Dans le concepteur DSL, cliquez avec le bouton droit sur la classe de domaine **ExampleModel** , pointez sur **Ajouter**, puis cliquez sur **DomainProperty**.

    1. Nommez la nouvelle propriété `DefaultNamespace` .

    2. Dans la fenêtre **Propriétés** de la nouvelle propriété, affectez à la **valeur par défaut la valeur** `DefaultNamespace` et affectez à **type** la valeur **String**.

2. Pour la classe de domaine **ExampleModel** , ajoutez une propriété de domaine nommée `CustomElements` .

     Dans la fenêtre **Propriétés** de la nouvelle propriété, affectez la valeur **calculé** à **genre** .

3. Pour la classe de domaine **ExampleElement** , ajoutez une propriété de domaine nommée `Namespace` .

     Dans la fenêtre **Propriétés** de la nouvelle propriété **, attribuez la valeur** **false** à la propriété, puis affectez à **type** la valeur **CustomStorage**.

4. Pour la classe de domaine **ExampleElement** , ajoutez une propriété de domaine nommée `IsNamespaceTracking` .

     Dans la **fenêtre Propriétés** de la nouvelle propriété **, attribuez** à la propriété la valeur **false**, affectez à la **valeur par défaut la valeur** `true` et affectez à **type** la valeur **Boolean**.

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Pour mettre à jour les éléments de diagramme et les détails DSL

1. Dans le concepteur DSL, cliquez avec le bouton droit sur la forme Geometry **ExampleShape** , pointez sur **Ajouter**, puis cliquez sur **Decorator de texte**.

    1. Nommez le nouvel élément décoratif de texte `NamespaceDecorator` .

    2. Dans la fenêtre **Propriétés** de l’élément décoratif de texte, définissez **position** sur **InnerBottomLeft**.

2. Dans le concepteur DSL, sélectionnez la ligne qui connecte la classe **ExampleElement** à la forme **ExampleShape** .

    1. Dans la fenêtre **Détails DSL** , sélectionnez l’onglet **mappages de décorateurs** .

    2. Dans la liste des éléments **décoratifs** , sélectionnez **NamespaceDecorator**, activez sa case à cocher, puis dans la liste des **propriétés d’affichage** , sélectionnez **espace de noms**.

3. Dans l' **Explorateur DSL**, développez le dossier **classes de domaine** , cliquez avec le bouton droit sur le nœud **ExampleElement** , puis cliquez sur **Ajouter un nouveau descripteur de type de domaine**.

    1. Développez le nœud **ExampleElement** , puis sélectionnez le nœud de **descripteur de type personnalisé (descripteur de type de domaine)** .

    2. Dans la fenêtre **Propriétés** du descripteur de type de domaine, affectez la valeur **true** à **code personnalisé** .

4. Dans l' **Explorateur DSL**, sélectionnez le nœud **comportement de sérialisation XML** .

    1. Dans la fenêtre **Propriétés** , définissez **chargement de publication personnalisé** sur **true**.

## <a name="transform-templates"></a>Modèles de transformation

Maintenant que vous avez défini les classes et les propriétés de domaine pour votre DSL, vous pouvez vérifier que la définition DSL peut être transformée correctement pour régénérer le code pour votre projet.

1. Dans la barre d’outils **Explorateur de solutions** , cliquez sur **transformer tous les modèles**.

2. Le système régénère le code pour la solution et enregistre DslDefinition. DSL. Pour plus d’informations sur le format XML des fichiers de définition, consultez [le fichier DslDefinition. DSL](../modeling/the-dsldefinition-dsl-file.md).

## <a name="create-files-for-custom-code"></a>Créer des fichiers pour du code personnalisé

Lorsque vous transformez tous les modèles, le système génère le code source qui définit votre langage spécifique à un domaine dans les projets DSL et DslPackage. Afin que vous puissiez éviter les interférences avec le texte généré, écrivez votre code personnalisé dans des fichiers qui sont distincts des fichiers de code générés.

Vous devez fournir du code pour conserver la valeur et l’état de votre propriété de suivi. Pour vous aider à distinguer votre code personnalisé du code généré et pour éviter les conflits de noms de fichiers, placez vos fichiers de code personnalisés dans un sous-dossier distinct.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DSL** , pointez sur **Ajouter**, puis cliquez sur **nouveau dossier**. Nommez le nouveau dossier `CustomCode` .

2. Cliquez avec le bouton droit sur le nouveau dossier **CustomCode** , pointez sur **Ajouter**, puis cliquez sur **nouvel élément**.

3. Sélectionnez le modèle **fichier de code** , définissez le **nom** sur `NamespaceTrackingProperty.cs` , puis cliquez sur **OK**.

     Le fichier NamespaceTrackingProperty. cs est créé et ouvert pour modification.

4. Dans le dossier, créez les fichiers de code suivants : `ExampleModel.cs,``HelperClasses.cs` , `Serialization.cs` et `TypeDescriptor.cs` .

5. Dans le projet **DslPackage** , créez également un `CustomCode` dossier et ajoutez-lui un `Package.cs` fichier de code.

## <a name="add-helper-classes-to-support-tracking-properties"></a>Ajouter des classes d’assistance pour prendre en charge les propriétés de suivi

Dans le fichier HelperClasses. cs, ajoutez les `TrackingHelper` `CriticalException` classes et comme suit. Vous allez référencer ces classes plus loin dans cette procédure pas à pas.

1. Ajoutez le code suivant au fichier HelperClasses. cs.

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

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>Ajouter du code personnalisé pour le descripteur de type personnalisé

Implémentez la `GetCustomProperties` méthode pour le descripteur de type pour la `ExampleModel` classe de domaine.

> [!NOTE]
> Code généré par les outils DSL pour le descripteur de type personnalisé pour les `ExampleModel` appels `GetCustomProperties` ; Toutefois, les outils DSL ne génèrent pas de code qui implémente la méthode.

La définition de cette méthode crée le descripteur de propriété de suivi pour la propriété de suivi d’espace de noms. En outre, fournir des attributs pour la propriété Tracking permet à la fenêtre **Propriétés** d’afficher la propriété correctement.

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Pour modifier le descripteur de type pour la classe de domaine ExampleModel

1. Ajoutez le code suivant au fichier TypeDescriptor. cs.

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

## <a name="adding-custom-code-for-the-package"></a>Ajout de code personnalisé pour le package

Le code généré définit un fournisseur de description de type pour la classe de domaine ExampleElement ; Toutefois, vous devez ajouter du code pour indiquer à la solution DSL d’utiliser ce fournisseur de description de type.

1. Ajoutez le code suivant au fichier Package. cs.

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

## <a name="add-custom-code-for-the-model"></a>Ajouter du code personnalisé pour le modèle

Implémentez la `GetCustomElementsValue` méthode pour la `ExampleModel` classe de domaine.

> [!NOTE]
> Code généré par les outils DSL pour les `ExampleModel` appels `GetCustomElementsValue` ; Toutefois, les outils DSL ne génèrent pas de code qui implémente la méthode.

La définition de la `GetCustomElementsValue` méthode fournit la logique pour la propriété calculée CustomElements de `ExampleModel` . Cette méthode compte le nombre de `ExampleElement` classes de domaine qui ont une propriété de suivi d’espace de noms qui a une valeur mise à jour par l’utilisateur et retourne une chaîne qui représente ce nombre comme une proportion du nombre total d’éléments dans le modèle.

En outre, ajoutez une `OnDefaultNamespaceChanged` méthode à `ExampleModel` et substituez la `OnValueChanged` méthode de la `DefaultNamespacePropertyHandler` classe imbriquée de `ExampleModel` à Call `OnDefaultNamespaceChanged` .

Étant donné que la propriété DefaultNamespace est utilisée pour calculer la propriété de suivi d’espace de noms, `ExampleModel` doit notifier toutes les `ExampleElement` classes de domaine que la valeur de DefaultNamespace a changé.

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Pour modifier le gestionnaire de propriétés pour la propriété suivie

1. Ajoutez le code suivant au fichier ExampleModel. cs.

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

## <a name="add-custom-code-for-the-tracking-property"></a>Ajouter du code personnalisé pour la propriété Tracking

Ajoutez une `CalculateNamespace` méthode à la `ExampleElement` classe de domaine.

La définition de cette méthode fournit la logique pour la propriété calculée CustomElements de `ExampleModel` . Cette méthode compte le nombre de `ExampleElement` classes de domaine qui ont une propriété de suivi d’espace de noms qui est dans l’État mis à jour par l’utilisateur, et retourne une chaîne qui représente ce nombre comme une proportion du nombre total d’éléments dans le modèle.

Ajoutez également un stockage pour les méthodes, et pour obtenir et définir, la propriété de stockage personnalisé d’espace de noms de la `ExampleElement` classe de domaine.

> [!NOTE]
> Le code généré par les outils DSL pour `ExampleModel` appelle les méthodes obtenir et définir ; toutefois, les outils DSL ne génèrent pas de code qui implémente les méthodes.

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Pour ajouter la méthode pour le descripteur de type personnalisé

1. Ajoutez le code suivant au fichier NamespaceTrackingProperty. cs.

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

## <a name="add-custom-code-to-support-serialization"></a>Ajouter du code personnalisé pour prendre en charge la sérialisation

Ajoutez du code pour prendre en charge le comportement de rechargement personnalisé pour la sérialisation XML.

> [!NOTE]
> Le code généré par les outils DSL appelle les `OnPostLoadModel` `OnPostLoadModelAndDiagram` méthodes et ; Toutefois, les outils DSL ne génèrent pas de code qui implémente ces méthodes.

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Pour ajouter du code afin de prendre en charge le comportement de publication personnalisé

1. Ajoutez le code suivant au fichier Serialization. cs.

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

## <a name="test-the-language"></a>Tester le langage

L’étape suivante consiste à générer et exécuter le concepteur DSL dans une nouvelle instance de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] afin que vous puissiez vérifier que la propriété de suivi fonctionne correctement.

1. Dans le menu **Générer**, cliquez sur **Régénérer la solution**.

2. Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.

    La build expérimentale de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] ouvre la solution de **débogage** , qui contient un fichier de test vide.

3. Dans **Explorateur de solutions**, double-cliquez sur le fichier test. trackingPropertyDsl pour l’ouvrir dans le concepteur, puis cliquez sur l’aire de conception.

    Notez que dans la fenêtre **Propriétés** du diagramme, la propriété **espace de noms par défaut** est **DefaultNamespace** et la propriété **éléments personnalisés** est **0/0**.

4. Faites glisser un élément **ExampleElement** de la **boîte à outils** vers la surface du diagramme.

5. Dans la fenêtre **Propriétés** de l’élément, sélectionnez la propriété **espace de noms** de l’élément et remplacez la valeur de **DefaultNamespace** par **OtherNamespace**.

    Notez que la valeur de l' **espace de noms d’élément** est maintenant affichée en gras.

6. Dans la fenêtre **Propriétés** , cliquez avec le bouton droit sur **espace de noms** de l’élément, puis cliquez sur **Réinitialiser**.

    La valeur de la propriété est changée en **DefaultNamespace**, et la valeur est affichée dans une police normale.

    Cliquez à nouveau avec le bouton droit sur l' **espace de noms** de l’élément. La commande de **réinitialisation** est maintenant désactivée, car la propriété est actuellement dans son état de suivi.

7. Faites glisser un autre **ExampleElement** de la **boîte à outils** vers la surface du diagramme, puis remplacez son espace de **noms d’élément** par **OtherNamespace**.

8. Cliquez sur l’aire de conception.

    Dans la fenêtre **Propriétés** du diagramme, la valeur des **éléments personnalisés** est maintenant **1/2**.

9. Remplacez la valeur de l' **espace de noms par défaut** du diagramme de **DefaultNamespace** par **NewNamespace**.

     L' **espace de noms** du premier élément effectue le suivi de la propriété d' **espace de noms par défaut** , tandis que l' **espace de noms** du deuxième élément conserve sa valeur de **OtherNamespace** mise à jour par l’utilisateur.

10. Enregistrez la solution, puis fermez la build expérimentale.

## <a name="next-steps"></a>Étapes suivantes

Si vous envisagez d’utiliser plusieurs propriétés de suivi ou si vous implémentez des propriétés de suivi dans plusieurs DSL, vous pouvez créer un modèle de texte pour générer le code commun pour la prise en charge de chaque propriété de suivi. Pour plus d’informations sur les modèles de texte, consultez [génération de code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [Guide pratique pour définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)
- [Guide pratique pour créer une solution de langage spécifique à un domaine](../modeling/how-to-create-a-domain-specific-language-solution.md)