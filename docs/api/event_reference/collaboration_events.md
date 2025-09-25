---
description: Events that are triggered when working with collaboration.
page_type: reference
editions:
    - experience
    - commerce
month_change: true
---

# Collaboration events

## Session management

The events below are dispatched when managing [collaborative editing sessions](../../content_management/collaborative_editing/collaborative_editing_guide.md):

| Event | Dispatched by |
|---|---|
|[BeforeCreateSessionEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Session-Event-BeforeCreateSessionEvent.html)| Collaboration Session Service |
|[CreateSessionEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Session-Event-CreateSessionEvent.html)| Collaboration Session Service |
|[BeforeUpdateSessionEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Session-Event-BeforeUpdateSessionEvent.html)| Collaboration Session Service |
|[UpdateSessionEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Session-Event-UpdateSessionEvent.html)| Collaboration Session Service |
|[BeforeDeleteSessionEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Session-Event-BeforeDeleteSessionEvent.html)| Collaboration Session Service |
|[DeleteSessionEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Session-Event-DeleteSessionEvent.html)| Collaboration Session Service |
|[JoinSessionEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Session-Event-JoinSessionEvent.html)| Collaboration Session Service |
|[LeaveSessionEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Session-Event-LeaveSessionEvent.html)| Collaboration Session Service |
|[SessionPublicPreviewEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Session-Event-SessionPublicPreviewEvent.html)| Collaboration Session Service |

## Invitation management

The events below are dispatched when managing collaboration invitations:

| Event | Dispatched by |
|---|---|
|[BeforeCreateInvitationEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Invitation-Event-BeforeCreateInvitationEvent.html)| Collaboration Invitation Service |
|[CreateInvitationEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Invitation-Event-CreateInvitationEvent.html)| Collaboration Invitation Service |
|[BeforeUpdateInvitationEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Invitation-Event-BeforeUpdateInvitationEvent.html)| Collaboration Invitation Service |
|[UpdateInvitationEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Invitation-Event-UpdateInvitationEvent.html)| Collaboration Invitation Service |
|[BeforeDeleteInvitationEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Invitation-Event-BeforeDeleteInvitationEvent.html)| Collaboration Invitation Service |
|[DeleteInvitationEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Invitation-Event-DeleteInvitationEvent.html)| Collaboration Invitation Service |

## Participant management

The events below are dispatched when managing collaboration participants:

| Event | Dispatched by |
|---|---|
|[BeforeAddParticipantEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Participant-Event-BeforeAddParticipantEvent.html)| Collaboration Participant Service |
|[AddParticipantEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Participant-Event-AddParticipantEvent.html)| Collaboration Participant Service |
|[BeforeUpdateParticipantEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Participant-Event-BeforeUpdateParticipantEvent.html)| Collaboration Participant Service |
|[UpdateParticipantEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Participant-Event-UpdateParticipantEvent.html)| Collaboration Participant Service |
|[BeforeRemoveParticipantEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Participant-Event-BeforeRemoveParticipantEvent.html)| Collaboration Participant Service |
|[RemoveParticipantEvent](/api/php_api/php_api_reference/classes/Ibexa-Contracts-Collaboration-Participant-Event-RemoveParticipantEvent.html)| Collaboration Participant Service |