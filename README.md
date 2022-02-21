### This App displays Cats Breed list from (https://thecatapi.com/) API in Grid, and on click of an item in grid, it makes another API call to get more details and images about the selected cat breed and displays it in a details screen. 


## Approach used

Code is written with clean swift (VIP) approach, which promotes clean architecture with testable code. More information can be found about this architecture over here https://clean-swift.com/

The view controller, interactor, and presenter are the three main components of Clean Swift. Also, we can have an optional router and worker.

### Scene

We have two Scene's in this Project, CatsList & CatsDetails. Each scene has VIP classes to perform their task. Both the scene test cases have been covered as well.

CatsList - 
- CatsBreedListViewController.swift - 
Defines a scene and contains a view or views, keeps instances of the interactor and router, And passes the actions from views to the interactor and takes the presenter actions as input to update UI.
- CatsBreedListInterator.swift - 
Contains a Scene’s business logic, keeps a reference to the presenter, and runs actions on workers based on input (from the View Controller), triggers and passes the output to the presenter.
- CatsBreedListPresenter.swift - 
Keeps a weak reference to the view controller that is an output of the presenter, after the interactor produces some results, it passes the response to the presenter. Also, if need the presenter marshals the response into view models suitable for display and then passes the view models back to the view controller for display to the user. We have done this for our CatsDetailPresenter. 
- CatsBreedListAPIWorker.swift - 
An abstraction that handles different under-the-hood operations like fetch the cats breed list from API through Network layer. 
- CatsBreedListRouter.swift - 
Extracts this navigation logic out of the view controller 

And we have similer structure for CatsDetails Scene as well. 


## Networking

Generic Networking layer is written so that it can be reused for any type of API call. Main API call is done in APILoader class which is generic class which confirms to APIHandler protocol, which handler the request(RequestHandler) & response(ResponseHandler).


## Scope of improvements 
- We can use SDWebImage or any other standard library for loading images instead of writing our extension for UIImageView, which can cause performance issue 
- UI can be improved in both the screens, in details screen we can show carousel of images for the selected breed 
- In VIP structure we are writing the setup of VIP in the router, we can write it in a different class and make the router more clean 
- Write more tests  for better code coverage 
- UI can be written in SwiftUI 
