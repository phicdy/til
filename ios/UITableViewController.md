https://developer.apple.com/reference/uikit/uitableviewcontroller

It implements UITableViewDelegate to configure table veiw.
https://developer.apple.com/reference/uikit/uitableviewdelegate

```swift
class MainViewController: UITableViewController {
    // Define row setting
    override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    }

    // Define action when each cell is selected
    override func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    }

    // Define num of selections in table view
    override func numberOfSections(in tableView: UITableView) -> Int {
    }

    // Define num of rows in selections in table view
    override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
    }

    // Define the behavior when each accesory button is tapped
    override func tableView(_ tableView: UITableView, accessoryButtonTappedForRowWith indexPath: IndexPath) {
    }
}
```
