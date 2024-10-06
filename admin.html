<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
    <title>Manage Data Bundles</title>
</head>
<body>
    <div class="container">
        <!-- Button to go back to the homepage -->
        <button class="btn btn-secondary my-4" onclick="goToHomepage()">Go to Homepage</button>

        <h1 class="my-4">Manage Data Bundles</h1>
        <table class="table table-striped">
            <thead>
                <tr>
                    <th>#</th>
                    <th>Title</th>
                    <th>Validity</th>
                    <th>Network Provider</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody id="bundles"></tbody>
        </table>
        <button class="btn btn-primary mt-4" data-bs-toggle="modal" data-bs-target="#bundleModal" onclick="openAddModal()">Add Bundle</button>
    </div>

    <!-- Modal for Adding/Editing Bundle -->
    <div class="modal fade" id="bundleModal" tabindex="-1" aria-labelledby="bundleModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="bundleModalLabel">Add Bundle</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <form id="bundleForm">
                        <div class="mb-3">
                            <label for="bundleTitle" class="form-label">Bundle Title</label>
                            <input type="text" class="form-control" id="bundleTitle" required>
                        </div>
                        <div class="mb-3">
                            <label for="bundleValidity" class="form-label">Validity</label>
                            <input type="text" class="form-control" id="bundleValidity" required>
                        </div>
                        <div class="mb-3">
                            <label for="networkProvider" class="form-label">Network Provider</label>
                            <select class="form-select" id="networkProvider" required>
                                <option value="" disabled selected>Select Network</option>
                                <option value="Safaricom">Safaricom</option>
                                <option value="Airtel">Airtel</option>
                                <option value="Telkom">Telkom</option>
                            </select>
                        </div>
                        <input type="hidden" id="bundleIndex">
                        <button type="submit" class="btn btn-primary">Save Bundle</button>
                    </form>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Redirect to homepage function
        function goToHomepage() {
            window.location.href = 'index.php'; // Replace with the correct URL for your homepage
        }

        // Load bundles from local storage or fallback to default data
        let bundlesToDisplay = JSON.parse(localStorage.getItem('bundles')) || [
            { title: '1.5GB @ Ksh 50', validity: 'Valid for 3 hours', provider: 'Safaricom' },
            { title: '350MB @ Ksh 49', validity: 'Valid for 7 days', provider: 'Airtel' },
            { title: '2.5GB @ Ksh 300', validity: 'Valid for 7 days', provider: 'Telkom' },
        ];

        // Function to render the bundles as table rows
        function renderBundles() {
            const container = document.getElementById('bundles');
            container.innerHTML = ''; // Clear existing content
            bundlesToDisplay.forEach((bundle, index) => {
                const row = `
                    <tr>
                        <td>${index + 1}</td>
                        <td>${bundle.title}</td>
                        <td>${bundle.validity}</td>
                        <td>${bundle.provider}</td>
                        <td>
                            <button class="btn btn-success btn-sm" onclick="openEditModal(${index})">Edit</button>
                            <button class="btn btn-danger btn-sm" onclick="confirmDeleteBundle(${index})">Delete</button>
                        </td>
                    </tr>
                `;
                container.innerHTML += row;
            });
        }

        // Open modal to add a new bundle
        function openAddModal() {
            document.getElementById('bundleForm').reset();
            document.getElementById('bundleModalLabel').textContent = 'Add Bundle';
            document.getElementById('bundleIndex').value = ''; // Clear hidden index
        }

        // Open modal to edit an existing bundle
        function openEditModal(index) {
            const bundle = bundlesToDisplay[index];
            document.getElementById('bundleTitle').value = bundle.title;
            document.getElementById('bundleValidity').value = bundle.validity;
            document.getElementById('networkProvider').value = bundle.provider;
            document.getElementById('bundleIndex').value = index;
            document.getElementById('bundleModalLabel').textContent = 'Edit Bundle';
            const modal = new bootstrap.Modal(document.getElementById('bundleModal'));
            modal.show();
        }

        // Handle form submission for adding/editing bundles
        document.getElementById('bundleForm').onsubmit = function (e) {
            e.preventDefault(); // Prevent default form submission
            const title = document.getElementById('bundleTitle').value;
            const validity = document.getElementById('bundleValidity').value;
            const provider = document.getElementById('networkProvider').value;
            const index = document.getElementById('bundleIndex').value;

            if (index === '') {
                // Add new bundle
                bundlesToDisplay.push({ title, validity, provider });
            } else {
                // Edit existing bundle
                bundlesToDisplay[index] = { title, validity, provider };
            }

            localStorage.setItem('bundles', JSON.stringify(bundlesToDisplay)); // Update local storage
            renderBundles(); // Re-render bundles
            const modal = bootstrap.Modal.getInstance(document.getElementById('bundleModal'));
            modal.hide(); // Hide modal
        };

        // Confirm before deleting a bundle
        function confirmDeleteBundle(index) {
            if (confirm("Are you sure you want to delete this bundle?")) {
                deleteBundle(index);
            }
        }

        // Delete bundle from the list
        function deleteBundle(index) {
            bundlesToDisplay.splice(index, 1); // Remove bundle from array
            localStorage.setItem('bundles', JSON.stringify(bundlesToDisplay)); // Update local storage
            renderBundles(); // Re-render bundles
        }

        renderBundles(); // Initial render
    </script>

    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.6/dist/umd/popper.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.min.js"></script>
</body>
