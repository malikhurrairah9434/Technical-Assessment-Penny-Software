# Implementation Notes


## 1. What I changed

- diff.util.ts

In the compute function only unit price were being compared so the change detection logic was not clear or incomplete so quantity was also compared in order to detect change"

*Reference:* https://stackoverflow.com/questions/1068834/object-comparison-in-javascript

- cr-detail.component.ts

Logic implemented in order to grant permissions to only approver and not the viewer.

Viewer can only see the requests buttons disable for it.

- cr-list.component.ts

In the change requests section the status listdown was not working implemented the function so it should display only selected status.

- cr-detail.component.ts

Approve Function Implemented now status is changed from pending to approved and also data is fetched from Mock API.

- cr-detail.component.ts

Reject function implemented, now status is changed to Rejected.

## 2. Component & state model

- A simple VieState Patter was used:
idle, loading, loaded and error
- Benifits:
Clear UI state transitions, easier error handeling and predictable rendering.
- Data Flow:
Component -> API service -> mock data
UI always reflects API response.

-

## 3. Invariants I keep


| Invariant | How / where |
|Only Approvers can take actions | can approve reject|
|Reject must include reason | Form Validations|
|Chronological Timeline | timeling getter sorted|
|Diff rows must be accurate | all fields comparison in computeDiff|


## 4. Testing strategy

- Relied on provided unit tests
- Correct detection of changed vs unchanged
- Manual testing: approve/reject flows, status updates etc
- Permission based UI behaviour

## 5. Assumptions

- Policies like cr_a_o imply approval permissions
- Mock API simulates backend behavior (state mutation   required)
- Status transitions:
- PENDING_APPROVAL → APPROVED / REJECTED
- Timeline entries use at as timestamp field
- Only relevant fields (quantity, unitPrice) define a "change"

## 6. Where I used AI

- Claude AI was used in verifying the logic and similar problems from Stackoverflow were also searched.

## 7. What I'd improve with more time

- I would improve the UI/UX of the product
- I would improved type safety
- I would optimize diff logic by making it extensible for more fields.