# pytorch-example

- 공부공부공부 !! ...


# Dataset Generator
```
from torch.utils.data import DataLoader, Dataset
class MyDataset(Dataset):
    def __init__(self, X, y=None, train=True, transforms=None):
        self.X = X
        self.y = y
        self.train=train
        self.transforms=transforms

    def __len__(self):
        return len(self.X)

    def __getitem__(self, idx):
        return_x, return_y = self.X[idx], self.y[idx]
        if self.transforms:
            return_x = self.transforms(return_x)
        if self.train:
            return return_x, return_y
        else:
            return return_x
            

train_dataset = MyDataset(X, y, train=True, transforms=transform)
train_loader = DataLoader(train_dataset, batch_size=batch_size, shuffle=True)
```

# GPU 

```
if torch.cuda.device_count() > 1:
    network = nn.DataParallel(network)
```
