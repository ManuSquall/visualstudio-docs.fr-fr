---
layout: LandingPage
title: Gestion de version dans Visual Studio | VSTS & TFS
description: Guide pour bien démarrer avec la gestion de version dans Visual Studio
keywords: VSTS, TFS, Gestion de version
author: steved0x
ms.manager: douge
ms.author: sdanie
ms.date: 12/15/2017
ms.topic: landing-page
ms.prod: .net-core
ms.assetid: 2c119a5f-0272-48c0-8d6c-806196944aea
ms.workload:
- multiple
ms.openlocfilehash: 428139af8680bc60f4456367d1a17d4c97874efc
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
ms.locfileid: "29795350"
---
# <a name="version-control-in-visual-studio"></a>Gestion de version dans Visual Studio

Les systèmes de gestion de version vous permettent de suivre les modifications apportées au code. À mesure que vous effectuez des modifications, le système de gestion de version prend une capture instantanée de vos fichiers. Le système de gestion de version enregistre cette capture instantanée définitivement afin que vous puissiez la rappeler ultérieurement si nécessaire. Visual Studio fournit [Git](/vsts/git/index) et [Contrôle de version Team Foundation (TFVC)](/vsts/tfvc/index). Pour choisir entre les deux systèmes, consultez [Choisir la gestion de version appropriée pour votre projet](/vsts/tfvc/comparison-git-tfvc?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json).

## <a name="git"></a>Git
Git est le système de gestion de version actuellement le plus utilisé, et devient rapidement la norme dans ce domaine. Git est un système de gestion de version distribué. Cela signifie que votre copie locale du code est un référentiel de gestion de version complet. Ces référentiels locaux complets facilitent le travail en mode hors connexion ou à distance. Vous validez votre travail localement, puis synchronisez votre copie du référentiel avec la copie sur le serveur. Ce paradigme diffère de la gestion de version centralisée où les clients doivent synchroniser le code avec un serveur avant de créer de nouvelles versions du code.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="https://www.visualstudio.com/learn-git/">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Découvrir Git</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/vsts/git/share-your-code-in-git-vs-2017?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Bien démarrer avec Git et Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/vsts/git/tutorial/clone?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Cloner un référentiel Git existant</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="tfvc"></a>TFVC

Le contrôle de version Team Foundation (TFVC, Team Foundation Version Control) est un système de contrôle de version centralisé. En général, les membres de l'équipe ont une seule version de chaque fichier sur leurs ordinateurs de développement. Les données d'historique sont conservées sur le serveur uniquement. Les branches sont basées sur le chemin d'accès et créées sur le serveur.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="/vsts/tfvc/overview">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Découvrir TFVC</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/vsts/tfvc/share-your-code-in-tfvc-vs?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Bien démarrer avec TFVC dans Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
   <li>
        <a href="/vsts/tfvc/get-code-reviewed-vs?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Vérifier votre code</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>


## <a name="resources"></a>Ressources 

- [Livre Pro Git](https://git-scm.com/book/en/v2)  
- [Planifier votre migration vers Git](https://www.visualstudio.com/learn/centralized-to-git/)  
- [Migrer de TFVC vers Git](https://www.visualstudio.com/learn/migrate-from-tfvc-to-git/)  

 

